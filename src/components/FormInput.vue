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
    <button
      class="btn"
      :disabled="!isValid"
      @click="add"
    >
      Добавить
    </button>
  </div>
</template>

<script>
export default {
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
  gap: 10px;
  padding: 20px;
  background: #0e9797;
  border-radius: 10px;
  box-shadow: 0px 4px 10px rgba(226, 168, 7, 0.1);
}

input {
  
  padding: 12px;
  width: 450px;
  border: 2px solid #6cbed3;
  border-radius: 8px;
  font-size: 16px;
  outline: none;
}

input:focus {
  border-color: #0056b3;
}

.btn {
  background: #007bff;
  color: white;
  font-size: 16px;
  padding: 10px 20px;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  transition: 0.3s;
}

.btn:hover {
  background: #0056b3;
}

.btn:disabled {
  background: #cccccc;
  cursor: not-allowed;
}
</style>
