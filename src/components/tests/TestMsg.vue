<template>
  <div>
    <div @click="msgs">{{ msg }}</div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      msg: "Строка",
    };
  },
  methods:{
    msgs(){
        this.msg = this.msg.split('').reverse().join("")+Math.floor(Math.random()*11)
        this.$emit('update', this.msg)
    }
  }
};
</script>

<style scoped> 

div {
  cursor: pointer;
  font-size: 20px;
  padding: 10px;
  user-select: none;
}
div:hover {
  color: blue;
}
</style>