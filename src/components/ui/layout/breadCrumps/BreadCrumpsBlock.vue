<script setup lang="ts">
import type { Link } from '@/types/LinkType'
import { RouterLink } from 'vue-router'

const routes: Link[] = [
  {
    href: '/none',
    content: 'Главная'
  },
  {
    href: '/',
    content: 'Новости и статьи'
  }
]
</script>

<template>
  <div class="bread-crumps">
    <RouterLink v-for="(route, index) in routes" :key="index" :to="route.href" class="bread-crumps-link">
      {{ route.content }}
      <span v-if='index !== routes.length - 1'>/</span>
    </RouterLink>
  </div>
</template>

<style scoped lang='scss'>
.bread-crumps {
	background-color: #262626;
	display: flex;
	justify-content: flex-start;
	gap: 0.5rem;
	padding: 0.5% 5%;
	&-link {
		display: flex;
		gap: 0.5rem;
		color: #D9D9D9;
		font-size: clamp(6px, 2vw, 12px);
	}
}

.router-active-link {
  color: #ffffff;
}
</style>