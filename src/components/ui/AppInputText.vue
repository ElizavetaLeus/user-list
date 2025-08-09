<template>
  <input 
    type="text"
    :value="value"
    :class="$style.input"
    :placeholder="placeholder"
    @input="handlerInput($event)">
</template>

<script setup>
defineProps({
  placeholder: {
    type: String,
    default: 'Поиск',
  },
  value: {
    type: String,
    default:'',
  }
})

const emits = defineEmits(['input'])

const handlerInput = (event)=>{
  emits('input', event.target.value)
}
</script>

<style module>
.input {
  width: 100%;
  max-height: 40px;
  padding: 11px 13px;
  border-radius: 5px;
  background-color: var(--color-white);
  font-weight: 400;
  font-size: 14px;
  line-height: 14px;
  
}
</style>