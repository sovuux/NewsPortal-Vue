<script setup lang="ts">
import DefaultLayout from '@/components/ui/layout/DefaultLayout.vue'
import { RouterView } from 'vue-router'
</script>

<template>
  <DefaultLayout>
    <template #layoutContent>
      <RouterView></RouterView>
    </template>
  </DefaultLayout>
</template>
