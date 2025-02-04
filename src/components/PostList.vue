<template>
<div>
    <post-item :post="post" class="post" v-for="post in posts" :key="post.id" />
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