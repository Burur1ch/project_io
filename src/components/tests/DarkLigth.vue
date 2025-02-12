<template>
    <div class="full">
      <span v-for="(krio, index) in EveryText" :style="{ color: krio.color }" :key="index">
        {{ krio.letter }}
      </span>
      <div class="main" @click="changeColor" :class="{ active: isOn }">
        <div class="circle"></div>
      </div>
    </div>
</template>
  
<script>
export default {
  data() {
    return {
      isOn: false,
      text: "Splited Words!"
    };
  },
  methods: {
    changeColor() {
      this.isOn = !this.isOn;
      this.$emit('changeColor', this.isOn)
    },
  },
  computed: {
    EveryText() {
      return this.text.toUpperCase().split('').map(letter => ({
        letter: letter,
        color: `hsl(${Math.random() * 100}, 100%, 50%)`
      }));
    }
  }
};
</script>
  
  <style scoped>
.full {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 600px;
}

.main {
  width: 60px;
  height: 30px;
  border-radius: 15px;
  background: black;
  display: flex;
  align-items: center;
  justify-content: flex-start; /* Стартовая позиция */
  padding: 2px;
  cursor: pointer;
  transition: background 0.3s ease-in-out, border 0.3s ease-in-out;
  border: 2px solid black; /* Убрали резкие изменения */
  box-sizing: border-box;
}

.main.active {
  background: white;
  justify-content: flex-end;
}

.circle {
  width: 24px;
  height: 24px;
  background: white;
  border-radius: 50%;
  transition: background 0.3s ease-in-out;
}

.main.active .circle {
  background: red;
}
</style>
  