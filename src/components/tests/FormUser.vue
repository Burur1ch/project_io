<template>
  <div>
    <form @submit.prevent="">
        <input placeholder="Enter name" v-model="output">
        <button :disabled="!output" @click="enter">Отправить</button>
    </form>
  </div>
</template>

<script>
export default {
    data(){
        return{
            output:''
        }
    }
    ,methods:{
        enter(){
            this.$emit('get', this.output)
        }
    }
}
</script>

<style>

</style>