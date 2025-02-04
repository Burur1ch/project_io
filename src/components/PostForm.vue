<template>
     <form @submit.prevent>
      <h3>Create post</h3>
      <my-input v-model="post.title" type="text" placeholder=" Naming "/>
      <my-input v-model="post.body" type="text" placeholder=" descr "/>
      <my-button style="margin-top:15px; align-self: end; ;" @click="createPost"> Create </my-button>
    </form>
</template>

<script>
import MyButton from './UI/MyButton.vue'
import MyInput from './UI/MyInput.vue'
export default {
  components:{
    MyButton,
    MyInput
  },
  data(){
    return{
        post:{
        title:"",
        body:""
      }
    }
  },
  methods:{
    createPost(){
    const newPost = { ...this.post, id: Date.now() }
    this.$emit('create', newPost)
    this.post={
      title:'',
      body:''
    }
    }
  }
}
</script>

<style>


.form {
  display: flex;
  flex-direction: column;
}

</style>