<template>
  <form @submit.prevent>
    <h4>Create post</h4>
    <my-input
      class="input" 
      v-model="post.title"
      type="text" 
      placeholder="Title"
    />
    <my-input
      class="input"
      v-model="post.body"
      type="text" 
      placeholder="Body"
    />
    <my-button 
      @click="createPost"
      >
      Create
    </my-button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      post: {
        title: '',
        body: ''
      }
    }
  },
  methods: {
    createPost() {
      this.post.id = Date.now();
      this.$emit('create', this.post)
      this.post = {
        title: '',
        body: ''
      }
    }
  }
}
</script>

<style scoped>
form {
  display: flex;
  flex-direction: column;
}
.input  {
  margin-top: 10px;
  padding-left: 10px;
}
</style>