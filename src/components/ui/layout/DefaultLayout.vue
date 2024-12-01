<script setup lang="ts">
import Header from '@/components/ui/layout/header/CommonHeader.vue'
import BreadCrumpsBlock from './breadCrumps/BreadCrumpsBlock.vue'
import CommonFooter from './footer/CommonFooter.vue'
</script>

<template>
  <div>
    <Header />
    <BreadCrumpsBlock />
    <slot name="layoutContent" />
    <CommonFooter />
  </div>
</template>