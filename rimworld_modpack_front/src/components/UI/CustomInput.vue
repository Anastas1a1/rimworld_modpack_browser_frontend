<template>
    <input :value="modelValue" @input="updateInput" class="input" type="text">
  </template>
  
  <script>
  export default {
    name: 'custom-input',
    props: {
      modelValue: [String, Number]
    },
    methods: {
      updateInput(event) {
        this.$emit('update:modelValue', event.target.value)
      }
    }
  }
  </script>
  
  <style scoped>
.input {
  width: 100%;
  border: 2px solid aliceblue;
  padding: 10px 15px;
  margin-bottom: 20px;
  border-radius: 15px;
  background-color: #8589AC;

}
  
  </style>