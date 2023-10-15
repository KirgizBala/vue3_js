<template>
  <div class="app">
    <h1 class="text-center">Post List</h1>
    <div class="app__btns">
      <my-button @click="showCreate" class="btn btn-secondary mx-auto">
        Create Task
      </my-button>
    </div>
    <my-select v-model="selectedSort" />
    <my-dialog v-model:show="createVisible">
      <post-form @create="createPost" />
    </my-dialog>
    <post-list :posts="sortedPost" @remove="removePost" v-if="!isPostsLoading" />
    <div v-else>Loading...</div>
  </div>
</template>

<script>
import PostForm from './components/PostForm.vue';
import PostList from '@/components/PostList.vue';
import MyButton from './components/UI/MyButton.vue';
import axios from 'axios';
import MySelect from './components/UI/MySelect.vue';

export default {
  components: {
    MySelect,
    MyButton,
    PostForm,
    PostList
  },
  data() {
    return {
      posts: [],
      createVisible: false,
      isPostsLoading: false,
      selectedSort: 'title',
    }
  },
  methods: {
    createPost(post) {
      this.posts.push(post);
      this.createVisible = false;
    },
    removePost(post) {
      this.posts = this.posts.filter(p => p.id !== post.id);
    },
    showCreate() {
      this.createVisible = true;
    },
    changePost(changedPost) {
      console.log(changedPost)
      this.posts.forEach(post => {
        if (post.id === changedPost.id) {
          post = changedPost;
        }
      })
    },
    async fetchPosts() {
      try {
        this.isPostsLoading = true;
        const response = await axios.get('https://jsonplaceholder.typicode.com/posts', { params: { _limit: 10 } });
        this.posts = response.data;
      } catch (e) {
        console.error(e);
      } finally {
        this.isPostsLoading = false;
      }
    }
  },
  mounted() {
    this.fetchPosts();
  },
  computed: {
    sortedPost() {
      return [...this.posts].sort((post1, post2) => post1[this.selectedSort]?.localeCompare(post2[this.selectedSort]))
    }
  },
}

</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.app {
  padding: 20px;
  height: 200px;
  width: 100%;
}

.app__btns {
  margin: 15px 0;
  display: flex;
  justify-content: space-between;
}
</style>

