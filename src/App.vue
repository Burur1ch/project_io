<template>
  <div
    class="container"
    :style="{ backgroundColor: smth ? '#b1d3c2' : '#006475' }"
  >
    <dark-ligth @changeColor="changeBack"></dark-ligth>
    <massive-item :exp="exp" />
    <form-input @create="add" />
  </div>
</template>

<script>
import FormInput from "./components/FormInput.vue";
import MassiveItem from "./components/MassiveItem.vue";
import DarkLigth from "./components/tests/DarkLigth.vue";

export default {
  components: { FormInput, MassiveItem, DarkLigth },
  data() {
    return {
      exp: [
        { number: 1, name: "Ведущий", weight: 600 },
        { number: 2, name: "Фотограф", weight: 400 },
        { number: 3, name: "Усадьба", weight: 800 },
      ],
      storage: "",
      smth: false,
    };
  },
  methods: {
    add(newExpense) {
      this.exp.push(newExpense);
    },
    getname(output) {
      this.storage = output;
    },
    changeBack(isOn) {
      this.smth = isOn;
    },
  },
};
</script>

<style >
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}



.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 20px;
  padding: 30px;
  background: #006475;
  min-height: 100vh;
}
</style>
