<template>
  <div>
    <AppIcon  :icon="icons.userIcon"
              :size="20"
    />
  </div>
</template>

<script setup lang="ts">
import { icons } from '@/icons/icons';
import AppIcon from '@/components/ui/AppIcon.vue';
</script>

<style module>

</style>