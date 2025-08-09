<template>
  <div :class="$style.filterUsers">
    <div :class="$style.buttonList">
      <AppButton 
        v-for="button in buttonList"
        :key="button.id"
        :text="button.text"
        :isActive="button.isActive"
        :color="button.color"
        :role="button.color"
        @click="setActiveButton(button.role)"
      />
    </div>
    <AppInputText
      :class="$style.inputText"
      :value="inputValue" 
      @input="setInputValue($event)"
    />
  </div>
</template>

<script setup>
import { ref } from 'vue';
import AppButton from '@/components/ui/AppButton.vue';
import AppInputText from '@/components/ui/AppInputText.vue';

const inputValueLocal = ref('');
defineProps({
  inputValue: {
    type: String,
    required: true,
  }
})
const emits = defineEmits(['filterUsers']);
const buttonList = ref ([
  { id: 1, text: 'Все пользователи', isActive: true, color: 'blue', role: 'all' },
  { id: 2, text: 'Админы', isActive: false, color: 'pink', role: 'admin' },
  { id: 3, text: 'Редакторы', isActive: false, color: 'violet', role: 'editor' }
]);

const filterUsers = (params) => {
  emits('filterUsers', params)
}
const setActiveButton = (role) => {
  buttonList.value = buttonList.value.map((button) => {
    button.isActive = false;
    if (button.role === role) {
      button.isActive = true;
    }
    return button;
  })

  filterUsers({ type: 'UserRole', value: role });
}
const setInputValue = (value) => {
  inputValueLocal.value = value;
  filterUsers({ type: 'InputValue', value: inputValueLocal.value });
}
</script>

<style module>
.filterUsers {
  display: flex;
  justify-content: space-between;
}
.buttonList {
  display: flex;
  gap: 20px;
}
.inputText {
  max-width: 266px;
}
</style>