<template>
  <div class="expense-list">
    <div class="item" v-for="item in exp" :key="item.number">
      <div class="item-info">
        <strong>📌 Название:</strong> {{ item.name }}
        <br />
        <strong>💰 Стоимость:</strong> {{ item.weight }}$
      </div>
      <my-button class="btn-delete" @click="$emit('deleted', item.number)">
        🗑 Удалить
      </my-button>
    </div>
    <div class="total">
      <strong>Общая сумма:</strong> {{ totalAmount }} $
    </div>
  </div>
</template>

<script>
import MyButton from "./UI/MyButton.vue";

export default {
  components: { MyButton },
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
  gap: 15px;
  width: 100%;
  max-width: 650px;
  padding: 20px;
  background: #f8f9fa;
  border-radius: 12px;
  box-shadow: 0px 4px 12px rgba(0, 0, 0, 0.1);
}

.item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 15px;
  border-radius: 8px;
  background: white;
  box-shadow: 0px 2px 6px rgba(0, 0, 0, 0.1);
  transition: all 0.3s ease;
}

.item:hover {
  transform: translateY(-2px);
  box-shadow: 0px 4px 12px rgba(0, 0, 0, 0.15);
}

.item-info {
  font-size: 16px;
  color: #333;
}

.btn-delete {
  background: linear-gradient(135deg, #ff4d4d, #cc0000);
}

.btn-delete:hover {
  background: linear-gradient(135deg, #cc0000, #990000);
}

.total {
  margin-top: 10px;
  padding: 18px;
  font-size: 20px;
  font-weight: bold;
  text-align: center;
  color: white;
  border-radius: 10px;
  background: linear-gradient(135deg, #ffcc00, #ff9900);
  box-shadow: 0px 4px 10px rgba(255, 153, 0, 0.3);
  transition: all 0.3s ease-in-out;
}

.total:hover {
  background: linear-gradient(135deg, #ff9900, #ff6600);
}
</style>
