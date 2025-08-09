<template>
  <button
    :class="buttonClassList"
    :isActive="isActive"
    :color="color"
    @click="emitListener()"
  >
    {{ text }}
  </button>
</template>

<script setup lang="ts">
import { computed, useCssModule } from 'vue';

interface Props {
  text: string;
  isActive?: boolean;
  color?: string;
}
const props = withDefaults(defineProps<Props>(), {
  isActive: false,
  color: 'blue',
});

const emits = defineEmits(['click']);
const $style = useCssModule();

const buttonClassList = computed(() => {
  return [
    $style.button,
    props.isActive && $style.buttonActive,
    props.color === 'pink' && $style.buttonPink,
    props.color === 'violet' && $style.buttonViolet
  ]
})
const emitListener = () => {
  emits('click');
}
</script>

<style module>
/* базовая кнопка */
.button {
  --color-button: var(--color-blue);
  color: var(--color-button);
  border-color: var(--color-button);
  padding: 13px 20px;
  border-radius: 99px;
  background-color: transparent;
  border-width: 1px;
  border-style: solid;
  cursor: pointer;
  transition: 0.3s;
}
.button:hover {
  opacity: 90%;
}
/* фиолетовая кнопка */
.buttonViolet {
  --color-button: var( --color-violet);
}
.buttonViolet:hover {
  opacity: 90%;
}
/* розовая кнопка */
.buttonPink {
  --color-button: var( --color-pink);
}
.buttonPink:hover {
  opacity: 90%;
}
/* активная кнопка */
.buttonActive {
  background-color: var(--color-button);
  color: var(--color-white);
}
</style>