<template>
  <div class="container">
    <h1 :class="$style.title">Пользователи</h1>
    <div :class="$style.filterUsers">
      <FilterUsers
        :inputValue="filters.query"
        @filterUsers="setFilters($event)"
      />
    </div>
    <div :class="$style.userCards">
      <UserCard 
        v-for="user in userList"
        :key="user.id"
        :user="user"
      />
    </div>
  </div>
</template>

<script setup lang="ts">
import UserCard from '@/components/ui/UserCard.vue';
import { ref } from 'vue';
import FilterUsers from '@/components/FilterUsers.vue';
import { computed } from 'vue';

const userListDefault = [
  { id: 1001, name: 'Ваня', role: 'user' },
  { id: 1002, name: 'Ваня', role: 'admin' },
  { id: 1003, name: 'Петя', role: 'admin' },
  { id: 1004, name: 'Евкакий', role: 'editor' },
  { id: 1005, name: 'Пупа', role: 'user' },
  { id: 1006, name: 'Лупа', role: 'user' }
];
const filters = ref({
  role: 'all',
  query: '',
})


const setFilters = (params) => {
  if (params.type === 'InputValue') {
    filters.value.query = params.value;
  }
  if (params.type === 'UserRole') {
    filters.value.role = params.value;
  }
}
const userList = computed(() => {
  return userListDefault.filter((user) => {
    const hasUserRole = user.role===filters.value.role || filters.value.role === 'all';
    const hasUserNameQuery = user.name.toLowerCase().includes(filters.value.query.toLowerCase());
    
    return hasUserRole && hasUserNameQuery;
  })
})
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
.userCards {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr 1fr;
  gap: 30px;
  margin-top: 30px;
}
@media screen and (max-width: 1280px) {
  .userCards {
  grid-template-columns: 1fr 1fr 1fr;
  }
}

@media screen and (max-width: 925px) {
  .userCards {
    grid-template-columns: 1fr 1fr;
  }
}
@media screen and (max-width: 700px) {
  .userCards {
    grid-template-columns: 1fr;
  }
}
</style>
