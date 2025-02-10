<template>
  <div>
    <div class="container">
      <input type="text" v-model="threads.name" placeholder="Введите имя">
      <input type="number" v-model="threads.price"  placeholder="Введите прайс">
      <button class="btn" v-show="this.threads.name!=='' && this.threads.price !== null" @click="add"> Добавить </button>
      <div class="item" v-for="item in exp" :key="item.number">
        <div><strong>Название траты: </strong>{{ item.name }}</div>
        <div><stong>Стоимость: </stong>{{ item.weight }}$</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      exp: [
        { number: 1, name: "Ведущий", weight: 600 },
        { number: 2, name: "Фотограф", weight: 400 },
        { number: 3, name: "Усадьба", weight: 800 },
      ],
      threads:{
        name:'', price: null
      }
    };
  },
  methods: {
    add(){
      this.exp.push({
        number: this.exp.length +1,
        name: this.threads.name,
        weight: this.threads.price
      })
      this.threads = { name: "", price: null };
    }
  },
};
</script>

<style>

input{
  padding: 15px;
  width: 400px;
  height: 50px;
  border: 2px solid blue;
  margin: 15px 0;
  font-size: 20px;
}

.btn{
  border:2px solid blue;
  margin: 10px 0;
  width: 100px;
  height: 50px;
}

.btn:hover{
  color:red;
  transform: scale(1.1);
  font-size: 18px;
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}
.item {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  font-size: 20px;
  padding: 15px;
  border: 2px solid gray;
  width: 800px;
  height: 100px;
}
</style>