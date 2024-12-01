<script setup lang="ts">
import HeaderMainMenu from '@/components/ui/layout/header/mainMenu/HeaderMainMenu.vue'
import HeaderTopPanel from '@/components/ui/layout/header/topPanel/HeaderTopPanel.vue'
</script>

<template>
  <header class='header'>
    <HeaderTopPanel />
    <HeaderMainMenu />
  </header>
</template>

<style scoped lang='scss'>
.header {
  width: 100%;
}
</style>