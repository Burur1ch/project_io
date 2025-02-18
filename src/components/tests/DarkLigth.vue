<template>
  <div class="full">
    <span
      v-for="(krio, index) in EveryText"
      :style="{ color: krio.color }"
      :key="index"
      class="letter"
    >
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
      this.$emit("changeColor", this.isOn);
    }
  },
  computed: {
    EveryText() {
      return this.text.toUpperCase().split("").map(letter => ({
        letter: letter,
        color: `hsl(${Math.random() * 360}, 100%, 60%)`
      }));
    }
  }
};
</script>

<style scoped>
/* Общий стиль контейнера */
.full {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 600px;
  padding: 20px;
  background: linear-gradient(135deg, #00334e, #008080, #34a853, #2c6e49);
  background-size: 300% 300%;
  animation: gradientBG 10s ease infinite;
  border-radius: 12px;
  box-shadow: 0px 4px 20px rgba(0, 0, 0, 0.3);
}

/* Анимация для динамичного фона */
@keyframes gradientBG {
  0% {
    background-position: 0% 50%;
  }
  50% {
    background-position: 100% 50%;
  }
  100% {
    background-position: 0% 50%;
  }
}

/* Стилизация букв */
.letter {
  font-weight: bold;
  font-size: 22px;
  text-shadow: 2px 2px 6px rgba(0, 0, 0, 0.2);
  transition: transform 0.2s ease-in-out;
}

.letter:hover {
  transform: scale(1.1);
}

/* Стиль переключателя */
.main {
  width: 65px;
  height: 35px;
  border-radius: 18px;
  background: linear-gradient(135deg, #222, #555);
  display: flex;
  align-items: center;
  justify-content: flex-start;
  padding: 3px;
  cursor: pointer;
  transition: all 0.4s ease-in-out;
  border: 2px solid black;
  box-shadow: 0px 2px 10px rgba(0, 0, 0, 0.3);
}

/* Активный режим */
.main.active {
  background: linear-gradient(135deg, #ddd, #fff);
  justify-content: flex-end;
  box-shadow: 0px 2px 15px rgba(255, 0, 0, 0.5);
}

/* Стиль круга внутри переключателя */
.circle {
  width: 28px;
  height: 28px;
  background: white;
  border-radius: 50%;
  transition: background 0.3s ease-in-out, transform 0.3s ease-in-out;
  box-shadow: 0px 2px 6px rgba(0, 0, 0, 0.3);
}

.main.active .circle {
  background: red;
  transform: scale(1.1);
}

/* Адаптивность */
@media (max-width: 768px) {
  .full {
    width: 100%;
    flex-direction: column;
    gap: 20px;
  }
}
</style>
