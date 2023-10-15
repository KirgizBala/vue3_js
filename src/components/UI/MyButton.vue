<template>
  <button class="btn btn-secondary">
    <slot></slot>
  </button>
</template>

<script>
export default {
  name: 'my-button'
}
</script>

<style scoped>
.btn {
  margin: 10px;
}
</style>