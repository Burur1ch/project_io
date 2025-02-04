<template>
  <div>
    <div class="dialog" v-if="show" @click="hideDialog">
      <div @click.stop class="dialog-content">
        <slot></slot>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "new-dialog",
  props: {
    show: {
      type: Boolean,
      default: false,
    },
  },
  methods:{
    hideDialog(){
        this.$emit('update:show',false )
    }
  }
};
</script>

<style scoped>
    .dialog{
        top: 0;
        right: 0;
        left: 0;
        bottom: 0;
        background: rgba(0,0,0,0.5);
        position: fixed;
        display: flex;
    }

    .dialog-content{
        margin: auto;
        background: white;
        border-radius: 12px;
        min-height: 60px;
        min-width: 300px;
        padding: 20px;
    }

</style>