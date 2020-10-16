<template>
  <div id="conversation-wrapper">
    <div id="conversation">
      <p class="comment" v-for="(c, i) in conversations" v-bind:key="i.toFixed()">
        {{ toUserName(c.who) }}: {{ c.comment }}
      </p>
    </div>
  </div>
</template>

<script>
import { enumWho } from '../App.vue';

export default {
  props: {
    conversations: {
      type: Array,
      required: true,
      default: () => [],
    },
  },
  methods: {
    toUserName(who) {
      return who === enumWho.user ? 'you' : 'chatbot';
    }
  }
}
</script>

<style>
#conversation-wrapper {
  padding: 0 100px;
}
#conversation {
  background-color: #333;
  border-radius: 4px;
  padding: 20px 30px;
}
.comment {
  padding: 5px 0;
}
</style>
