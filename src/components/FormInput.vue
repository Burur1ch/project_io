<template>
  <div class="model">
    <input 
      type="text" 
      v-model="threads.name" 
      placeholder="Введите название" 
    />
    <input 
      type="number" 
      v-model="threads.price" 
      placeholder="Введите стоимость" 
    />
    <my-button
      class="btn"
      :disabled="!isValid"
      @click="add"
    >
      ➕ Добавить
    </my-button>
  </div>
</template>

<script>
import MyButton from './UI/MyButton.vue';
export default {
  components: { MyButton },
  data() {
    return {
      threads: {
        name: "",
        price: null,
      },
    };
  },
  computed: {
    isValid() {
      return this.threads.name.trim() !== "" && this.threads.price > 0;
    },
  },  
  methods: {
    add() {
      if (!this.isValid) return;

      const newExpense = {
        number: Date.now(),
        name: this.threads.name,
        weight: this.threads.price,
      };

      this.$emit("create", newExpense);
      this.threads = { name: "", price: null };
    },
  },
};
</script>

<style scoped>
.model {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 20px;
  padding: 25px;
  background: linear-gradient(135deg, #0e9797, #007bff);
  border-radius: 12px;
  box-shadow: 0px 6px 12px rgba(0, 0, 0, 0.15);
  animation: fadeIn 0.3s ease;
}

input {
  padding: 12px;
  width: 450px;
  border: 2px solid #6cbed3;
  border-radius: 8px;
  font-size: 16px;
  outline: none;
  transition: border-color 0.3s ease, box-shadow 0.3s ease;
}

input:focus {
  border-color: #ffc107;
  box-shadow: 0px 4px 8px rgba(255, 193, 7, 0.25);
}

.btn:disabled {
  background: #ccc;
  cursor: not-allowed;
}

@keyframes fadeIn {
  from {
    opacity: 0;
    transform: scale(0.9);
  }
  to {
    opacity: 1;
    transform: scale(1);
  }
}
</style>
