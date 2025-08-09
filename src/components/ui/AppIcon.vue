<template>
  <div
    :class="$style.icon"
    :size="`--size ${size}px`"
    v-html="icon"
  ></div>
</template>

<script setup lang="ts">
defineProps({
  icon: {
    type: String,
    required: true,
  },
  size: {
    type: Number,
    default: 20,
  }
})
</script>

<style module>
.icon {
  width: var(--size);
  height: var(--size);
  display: flex;
  align-items: center;
  justify-content: center;
}
.icon svg {
  width: var(--size);
  height: var(--size);
}
</style>