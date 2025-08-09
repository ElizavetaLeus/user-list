<template>
  <div class="container">
    <h1 :class="$style.title">Пользователи</h1>
    <div :class="$style.filterUsers">
      <SetUsers 
        inputValue=""
      />
    </div>
    <UserIcon />
  </div>
</template>

<script setup lang="ts">
import SetUsers from '@/components/SetUsers.vue';
import UserIcon from '@/components/ui/UserIcon.vue';


</script>

<style module>
.title {
  font-size: 26px;
  line-height: 1;
  font-size: 400;
}
.filterUsers {
  margin-top: 40px;
}
</style>
