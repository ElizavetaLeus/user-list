<template>
  <div :class="$style.userCard">
    <div :class="userClassList">
      <AppIcon  :icon="icons.userIcon"
                :size="20"
      />
    </div>
    <div>{{ user.name }}</div>
  </div>
</template>

<script setup lang="ts">
import { icons } from '@/icons/icons';
import { computed, useCssModule } from 'vue';
import AppIcon from '@/components/ui/AppIcon.vue';

const props = defineProps({
  user: {
    type: Object,
    required: true,
  }
})
const userClassList = computed(() => {
  return [
    $style.userIconRole,
    props.user.role === 'admin' && $style.userIconAdmin,
    props.user.role === 'editor' && $style.userIconEditor
  ]
})
const $style = useCssModule();
</script>

<style module>
.userCard {
  background-color: var(--color-white);
  color: var(--color-black);
  padding: 5px;
  border-radius: 99px 10px 10px 99px;
  font-weight: 700;
  font-size: 14px;
  line-height: 14px;
  display: flex;
  gap: 15px;
  justify-content: flex-start;
  align-items: center;
}
.userIconRole {
  --user-color-by-role: var(--color-dark-gray-10);
  --color-icon-by-role: var(--color-dark-gray);
  width: 50px;
  height: 50px;
  border-radius: 50%;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: var(--user-color-by-role);
  color: var(--color-icon-by-role);
}
.userIconAdmin {
  --user-color-by-role: var(--color-pink);
  --color-icon-by-role: var(--color-white);
}
.userIconEditor {
  --user-color-by-role: var(--color-violet);
  --color-icon-by-role: var(--color-white);
}
</style>