<template>
  <div class="main">
    <button @click="change" :style="newbee">Press me for change color</button>
  </div>
</template>

<script>
export default {
    data(){
        return{
            isActive: false,
        }
    },
    computed:{
        newbee(){
            return {
                backgroundColor: this.isActive ? 'green' : 'red', 
                color: "white",
            }
        }
    },
    methods:{
        change(){
            this.isActive = !this.isActive
        }
    }
}
</script>

<style>

</style>