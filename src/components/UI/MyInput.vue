<template>
    <input 
      class="input" 
      :value="modelValue" 
      @input="$emit('update:modelValue', $event.target.value)" 
      v-bind="$attrs"
    />
  </template>
  
  <script>
  export default {
    props: {
      modelValue: [String, Number]
    }
  };
  </script>
  

<style>
.input {
  
  padding: 12px;
  width: 450px;
  border: 2px solid #6cbed3;
  border-radius: 8px;
  font-size: 16px;
  outline: none;
}

.input:focus {
  border-color: #0056b3;
}

</style>