<template>
  <div class="container" :style="{ backgroundColor: smth ? '#b1d3c2' : '#006475' }">
    <my-button class="btn-add" @click="show = true">➕ Добавить запись</my-button>

    <my-dialog :show="show" @close="show = false">
      <form-input @create="add" />
    </my-dialog>

    <dark-ligth @changeColor="changeBack"></dark-ligth>

    <massive-item v-if="exp.length > 0" :exp="exp" @deleted="deleted" />
    <div v-else class="empty-message">⚠️ Massive is empty</div>
  </div>
</template>

<script>
import FormInput from "./components/FormInput.vue";
import MassiveItem from "./components/MassiveItem.vue";
import MyDialog from "./components/MyDialog.vue";
import DarkLigth from "./components/tests/DarkLigth.vue";
import MyButton from "./components/UI/MyButton.vue";

export default {
  components: { FormInput, MassiveItem, DarkLigth, MyDialog, MyButton },
  data() {
    return {
      exp: [
        { number: 1, name: "Ведущий", weight: 600 },
        { number: 2, name: "Фотограф", weight: 400 },
        { number: 3, name: "Усадьба", weight: 800 },
      ],
      smth: false,
      show: false,
    };
  },
  methods: {
    add(newExpense) {
      this.exp.push(newExpense);
      this.show = false;
    },
    changeBack(isOn) {
      this.smth = isOn;
    },
    deleted(itemId) {
      this.exp = this.exp.filter((p) => p.number !== itemId);
    },
  },
};
</script>

<style>
*{
  margin: 0;
  padding: 0;
}
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 30px;
  padding: 40px;
  background: #006475;
  min-height: 100vh;
  transition: background 0.3s ease;
}

.btn-add {
  padding: 12px 24px;
  font-size: 18px;
  background: linear-gradient(135deg, #ffc107, #ff9800);
  color: #333;
  border-radius: 10px;
  border: none;
  cursor: pointer;
  box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.15);
  transition: all 0.3s ease;
}

.btn-add:hover {
  background: linear-gradient(135deg, #ff9800, #ff5722);
  transform: translateY(-2px);
}

.empty-message {
  color: red;
  font-size: 24px;
  font-weight: bold;
  background: rgba(255, 255, 255, 0.1);
  padding: 12px;
  border-radius: 8px;
}
</style>
