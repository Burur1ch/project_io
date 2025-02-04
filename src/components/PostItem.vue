<template>
<div>
    <div>
        <div><strong>Название: </strong>{{ post.title }}</div>
        <div><strong>Описание: </strong>{{ post.body }}</div>
    </div>
    <div class="post-btn">
        <my-button @click="$emit('remove',post)">Delete</my-button>
    </div>

</div>
          
</template>

<script>
import MyButton from './UI/MyButton.vue'
export default {
  components: { MyButton },
    props:{
        post:{
            type: Object,
            required: true
        }
    }
}
</script>

<style scoped>
.post{
    display: flex;
    align-items: center;
  padding: 15px;
  border: 2px solid teal;
  margin-top: 15px;
  justify-content: space-between;
}

</style>