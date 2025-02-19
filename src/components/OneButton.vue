<script setup>
defineProps({
  btnValue: String,
});
</script>

<template>
<div
  class="
    flex justify-center bg-btn-bg rounded-xs
    shadow-btn active:translate-0.5 active:shadow-none
  "
  @click="$emit('clickButton', btnValue)"
>
  <button class="text-white text-4xl leading-0 w-auto h-12">
    {{ btnValue }}
  </button>
</div>
</template>
