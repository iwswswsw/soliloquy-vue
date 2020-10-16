<template>
  <div id="comment-add">
    <form>
      <input id="input-comment" type="text" v-model="comment"/>
      <button id="button-add" v-on:click="handleClick">呟く</button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      comment: '',
    };
  },
  methods: {
    handleClick() {
      if (event) {
        event.preventDefault()
      }
      this.$emit('addComment', this.comment);
    },
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#comment-add {
  text-align: center;
  margin: 20px auto;
}
#input-comment {
  width: 400px;
}
#button-add {
  margin-left: 10px;
}
</style>
