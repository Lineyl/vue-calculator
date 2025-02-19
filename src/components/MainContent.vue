<script setup>
  import { ref } from "vue";
  import ButtonList from './ButtonList.vue'

  const displayValue = ref('')
  const inputValue = ref('')
  const operation = ref('')

  const onButtonClick = (value) => {
    if (value === 'C') {
      displayValue.value = ''
      inputValue.value = ''
      operation.value = ''
      return
    }

    if (['+', '-', 'X', '/'].includes(value)) {
      if (inputValue.value && !['+', '-', 'X', '/'].includes(inputValue.value.slice(-1))) {
        inputValue.value += value
        operation.value = value
      }
      return;
    }

    if (value === '=' && inputValue.value) {
      try {
        displayValue.value = eval(inputValue.value.replace('X', '*'))
        inputValue.value = displayValue.value.toString()
        operation.value = ''
      } catch {
        displayValue.value = 'err'
      }
    return;
    }

    if (operation.value) {
      inputValue.value += value
      displayValue.value = value
    } else {
      inputValue.value += value
      displayValue.value = inputValue.value
    }
  }
</script>

<template>
<section class="flex justify-center">
  <div class="max-w-90 mt-20 px-5 rounded-2xl bg-body-calc shadow-calc">
    <input
      v-model="displayValue"
      class="outline-0 mt-10 mb-7 px-1 py-0.5 bg-gray-100 text-5xl w-full box-border rounded-sm text-right"
    >
    <ButtonList @onButtonClick="onButtonClick"/>
  </div>
</section>
</template>
