<template>
  <div>
<div v-if="posts.length > 0">
    <post-item @remove="$emit('remove',post)" :post="post" class="post" v-for="post in posts" :key="post.id" />
</div>
<h2 v-else style="color: red;">Sorry something went wrong</h2>
</div>
</template>

<script>
import PostItem from './PostItem.vue'
export default {
  components: { PostItem },
  props: {
    posts: {
      type: Array,
      required: true, 
    }
  }
}
</script>

<style scoped>

</style>