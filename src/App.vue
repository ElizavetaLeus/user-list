<template>
  <div class="container">
    <h1 :class="$style.title">Пользователи</h1>
    <div :class="$style.filterUsers">
      <SetUsers 
        inputValue=""
      />
    </div>
    <UserCard 
      :userlist="userListDefault[0]"
      v-for="user in userListDefault"
      :key="user.id"
      :user="user"
    />
  </div>
</template>

<script setup lang="ts">
import SetUsers from '@/components/SetUsers.vue';
import UserCard from '@/components/ui/UserCard.vue';
// import { ref } from 'process';

const userListDefault = [
  { id: 1001, name: 'Ваня', role: 'user' },
  { id: 1002, name: 'Ваня', role: 'admin' },
  { id: 1003, name: 'Петя', role: 'admin' },
  { id: 1004, name: 'Евкакий', role: 'editor' },
  { id: 1005, name: 'Пупа', role: 'user' },
  { id: 1006, name: 'Лупа', role: 'user' }
];
// const filters = ref({
//   role: 'all',
//   query: '',
// })

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
