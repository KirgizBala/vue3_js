<template>
  <select @change="changeOption">
    <option disabled value="">sort by</option>
    <option v-for="option in sortOption" key="option.value" :value="option.value">
      {{ option.name }}
    </option>
  </select>
</template>

<script>
export default {
  name: 'my-select',
  data() {
    return {
      selectedSort: '',
      sortOption: [
        { value: 'title', name: 'title' },
        { value: 'body', name: 'body' },
      ]
    }
  },
  methods: {
    changeOption(event) {
      this.$emit('update:modelValue', event.target.value);
    }
  }
}
</script>

<style scoped></style>