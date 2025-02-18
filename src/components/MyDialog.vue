<template>
    <transition name="fade">
      <div class="dialog" v-if="show" @click.self="$emit('close')">
        <div class="dialog-container">
          <slot></slot>
        </div>
      </div>
    </transition>
  </template>
  
  <script>
  export default {
    props: {
      show: {
        type: Boolean,
        required: true,
      },
    },
  };
  </script>
  
  <style scoped>
  .dialog {
    top: 0;
    right: 0;
    left: 0;
    bottom: 0;
    background: rgba(0, 0, 0, 0.5);
    position: fixed;
    display: flex;
    backdrop-filter: blur(4px);
    z-index: 1000;
  }
  
  .dialog-container {
    margin: auto;
    background: #ffffff;
    border-radius: 14px;
    padding: 25px;
    box-shadow: 0px 8px 20px rgba(0, 0, 0, 0.25);
    animation: scaleUp 0.2s ease;
  }
  
  @keyframes scaleUp {
    from {
      transform: scale(0.8);
      opacity: 0;
    }
    to {
      transform: scale(1);
      opacity: 1;
    }
  }
  
  .fade-enter-active,
  .fade-leave-active {
    transition: opacity 0.3s;
  }
  .fade-enter, .fade-leave-to {
    opacity: 0;
  }
  </style>
  