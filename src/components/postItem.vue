<template>
  <div class="post">
    <div class="post__text">
      <div><strong>Title: </strong> {{ post.title }}</div>
      <div><strong>Body: </strong> {{ post.body }}</div>
    </div>
    <div class="post__btns">
      <my-button @click="$emit('remove', post)">
        Delete
      </my-button>
    </div>
  </div>
</template>

<script>

export default {
  props: {
    post: {
      type: Object,
      required: true,
    },
  },
}
</script>

<style scoped>
.post {
  display: flex;
  justify-content: space-between;
  padding: 15px;
  border: 2px solid teal;
  margin-top: 15px;
}

.post__text {
  display: flex;
  flex-direction: column;
  align-items: start;

}

.post__btns {
  display: flex;
  flex-direction: column;
  justify-content: flex-end;
}
</style>