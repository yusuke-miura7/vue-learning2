<script setup>

const props = defineProps({
  modelValue: String,
});
</script>

<template>
  <input
    :value="props.modelValue"
    @input="$emit('update:modelValue', $event.target.value)"
    style="padding: 1em; border-radius: 1em; margin: 0.5em"
  />
</template>