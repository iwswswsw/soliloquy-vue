<template>
  <div>
    <Header />
    <CommentAdd @addComment="addComment" />
    <Conversation :conversations="conversations" />
  </div>
</template>

<script>
import Header from './components/Header'
import CommentAdd from './components/CommentAdd'
import Conversation from './components/Conversation'

export const enumWho = {
  user: 0,
  chatbot: 1,
};

const cbComments = ['へぇ〜', 'なるほど', 'いいね', 'やりますねぇ', 'うん']
const getCbComment = () => (cbComments[Math.floor(Math.random() * Math.floor(cbComments.length))]);

export default {
  name: 'App',
  components: {
    Header,
    CommentAdd,
    Conversation,
  },
  data() {
    return {
      conversations: [],
    }
  },
  methods: {
    addCbComment() {
      const cbConversation = { who: enumWho.chatbot, comment: getCbComment() };
      this.conversations = [...this.conversations, cbConversation];
    },
    addComment(comment) {      
      console.log(comment);
      const userConversation = { who: enumWho.user, comment };
      this.conversations = [...this.conversations, userConversation];
      setTimeout(() => this.addCbComment(), 800);
    }
  },
}
</script>

<style>
@import "./styles/reset.scss";
</style>
