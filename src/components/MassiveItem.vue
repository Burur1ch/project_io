<template>
  <div class="expense-list">

    <div class="item" v-for="item in exp" :key="item.number">
      <div><strong>Название:</strong> {{ item.name }}</div>
      <div><strong>Стоимость:</strong> {{ item.weight }}$</div>
    </div>
    <div class="total">
      <strong>Общая сумма:</strong> {{ totalAmount }} $
    </div>
  </div>
</template>

<script>
export default {
  props: {
    exp: {
      type: Array,
      required: true,
    },
  },
  computed: {
    totalAmount() {
      return this.exp.reduce((sum, item) => sum + item.weight, 0);
    },
  },
};
</script>

<style scoped>
.expense-list {
  display: flex;
  flex-direction: column;
  gap: 10px;
  width: 100%;
  max-width: 600px;
}

.item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 15px;
  border-radius: 8px;
  background: white;
  box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.1);
  transition: 0.3s;
}

.item:hover {
  transform: translateY(-2px);
  box-shadow: 0px 6px 12px rgba(0, 0, 0, 0.15);
}

.total {
  margin-top: 10px; 
  padding: 15px;
  font-size: 18px;
  font-weight: bold;
  text-align: center;
  color: white;
  border-radius: 8px;
  background: blue;
}
</style>
