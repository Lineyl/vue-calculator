<script setup>
  import OneButton from "@/components/OneButton.vue";

  const buttons = [
    '7', '8', '9', '/',
    '4', '5', '6', 'X',
    '1', '2', '3', '-',
    '.', '0', '=', '+',
  ]

  const emit = defineEmits(['onButtonClick'])

  const onButtonClick = (btnValue) => {
    emit('onButtonClick', btnValue)
  }

</script>

<template>
  <div class="grid grid-cols-4 grid-rows-4 gap-5 mb-15 p-2">
    <OneButton
      v-for="(btnValue, index) in buttons"
      :key="index"
      :btnValue="btnValue"
      @clickButton="onButtonClick"
    />
    <OneButton @clickButton="onButtonClick" btnValue="C" class="col-span-2"/>
  </div>
</template>
