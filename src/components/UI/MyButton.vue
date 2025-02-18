<template>
  <button class="btn">
    <slot></slot>
  </button>
</template>

<script>
export default {};
</script>

<style scoped>
.btn {
  background: linear-gradient(135deg, #007bff, #0056b3);
  color: white;
  font-size: 16px;
  padding: 12px 24px;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  transition: all 0.3s ease-in-out;
  font-weight: bold;
  box-shadow: 0px 4px 8px rgba(0, 123, 255, 0.3);
}

.btn:hover {
  background: linear-gradient(135deg, #0056b3, #003f7f);
  box-shadow: 0px 6px 12px rgba(0, 123, 255, 0.4);
  transform: translateY(-2px);
}

.btn:active {
  transform: scale(0.98);
}

.btn:disabled {
  background: #cccccc;
  cursor: not-allowed;
  box-shadow: none;
}
</style>
