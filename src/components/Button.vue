<template>
  <div class="buttonContainer">
    <button @click="onClick()" :style="{ background: color }" class="btn">
      {{ text }}
    </button>
  </div>
</template>

<script>

export default {
  name: 'Button',
  props: {
    text: String,
    color: String
  },
  methods: {
    onClick() {
      this.$emit('btn-click')
    }
  }
}
</script>

<style scoped>
  .buttonContainer {
    display: flex;
    align-items: center;
  }
</style>