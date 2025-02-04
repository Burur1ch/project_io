<template>
  <div class="app">
    <h2>Page with posts</h2>
    <my-button style="margin: 15px 0;" @click="showDialog">
      Create post
    </my-button>
    <new-dialog v-model:show="dialogVisible">
      <PostForm @create="createPost" @cancel="dialogVisible = false" />
    </new-dialog>

    <PostList @remove="removePost" :posts="posts" />
  </div>
</template>

<script>
import PostForm from "./components/PostForm.vue";
import PostList from "./components/PostList.vue";
import MyButton from './components/UI/MyButton.vue';
import NewDialog from "./components/UI/NewDialog.vue";

export default {
  components: {
    PostForm,
    PostList,
    NewDialog,
    MyButton,
  },
  data() {
    return {
      posts: [
        { id: 1, title: "Java", body: "easy" },
        { id: 2, title: "Python", body: "Medium" },
        { id: 3, title: "Kotlin", body: "Hard" },
      ],
      dialogVisible: false,
    };
  },
  methods: {
    createPost(post) {
      this.posts.push(post);
      this.dialogVisible = false
    },
    removePost(post) {
      this.posts = this.posts.filter((p) => p.id !== post.id);
    },
    showDialog(){
      this.dialogVisible = true
    }
  },
};
</script>

<style >
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
.app {
  padding: 20px;
}
</style>
