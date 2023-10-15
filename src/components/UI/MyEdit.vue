<template>
  <div class="edit" v-if="show" @click.stop="hideEdit">
    <div @click.stop class="edit__content">
      <slot></slot>
    </div>
  </div>
</template>

<script>
export default {
  name: 'my-edit',
  props: {
    show: {
      type: Boolean,
      default: false
    }
  },
  methods: {
    hideEdit() {
      this.$emit('update:show', false)
    }
  }
}
</script>

<style scoped>
.dialog {
  top: 0;
  bottom: 0;
  right: 0;
  left: 0;
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  display: flex;
}

.dialog__content {
  margin: auto;
  background: white;
  border-radius: 12px;
  min-height: 50px;
  min-width: 300px;
  padding: 20px;
}
</style>