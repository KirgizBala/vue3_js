<template>
  <div v-if="posts.length > 0">
    <transition-group name="post-list">
      <post-item v-for="post in posts" :post="post" :key="post.id" @remove="$emit('remove', post)" />
    </transition-group>
  </div>
  <h2 class="no-post" v-else>
    You haven't written a post yet
  </h2>
</template>

<script>
import postItem from "@/components/postItem";
export default {
  components: { postItem },
  props: {
    posts: {
      type: Array,
      required: true
    },
  }
}
</script>

<style scoped>
.post-list-item {
  display: inline-block;
  margin-right: 10px;
}

.post-list-enter-active,
.post-list-leave-active {
  transition: all 0.4s ease;
}

.post-list-enter-from,
.post-list-leave-to {
  opacity: 0;
  transform: translateY(30px);
}

.post-list-move {
  transition: transform 0.4s ease;
}

.no-post {
  margin-top: 20px;
  font-size: large;
}
</style>