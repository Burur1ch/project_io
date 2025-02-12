<template>
  <div>
    <button @click="getMore">Увеличить</button>
    <button @click="getLess">Поменьшить</button>
  </div>
</template>

<script>
export default {
    data(){
        return{

        }
    },
    methods:{
        getMore(){
            this.$emit('getmore',+1)
        },
        getLess(){
            this.$emit('getless',-1)
        }
    }
}
</script>

<style>

</style>