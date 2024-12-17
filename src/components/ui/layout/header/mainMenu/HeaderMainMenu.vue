<script setup lang="ts">
import type { Link } from '@/types/LinkType'
import { RouterLink } from 'vue-router'
import Logo from '../../../../../../public/logo/logo.svg'

const navItems: Link[] = [
  { href: '/', content: 'ElcoreStore' },
  { href: '/none', content: 'ElcoreCloud' },
  { href: '/none', content: 'ElcoreIDE' },
  { href: '/none', content: 'Обучение и ресурсы ▼' },
  { href: '/none', content: 'Новости и статьи' }
]
</script>

<template>
  <div class="header-main">
    <RouterLink class="header-main-logo" to="/">
      <img :src="Logo" alt="logo" class='header-main-logo-icon' />
      <h1 class="header-main-logo-link">ElcorePLC</h1>
    </RouterLink>
    <nav class="header-main-nav">
      <RouterLink
        v-for="navItem in navItems"
        :key="navItem.href"
        :to="navItem.href"
        active-class="router-active-link"
        class="header-main-nav-link"
      >
        {{ navItem.content }}
      </RouterLink>
    </nav>
    <div class="header-main-burger">
      <i class="pi pi-bars" />
    </div>
  </div>
</template>

<style scoped lang="scss">
.header-main {
  background-color: #101010;
  color: white;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1% 5%;
  &-logo {
    display: flex;
    gap: clamp(0.2rem, 1vw, 1rem);
    font-size: clamp(12px, 1vw, 24px);
    user-select: none;
    &-icon {
      width: clamp(19px, 2vw, 38px);
      height: auto;
    }
    &-link {
      color: white;
      font-weight: bold;
    }
  }
  &-nav {
    display: flex;
    gap: clamp(0.5rem, 2vw, 2.5rem);
    &-link {
      color: white;
      font-size: clamp(9px, 1vw, 18px);
      font-weight: bold;
      transition:
        color 0.3s ease,
        background-color 0.3s ease;
      &:hover {
        color: #d9d9d9;
      }
    }
  }
  &-burger {
    display: flex;
    align-items: center;
    font-size: clamp(1rem, 2vw, 2rem);
    cursor: pointer;
    transition:
      color 0.3s ease,
      background-color 0.3s ease;
    &:hover {
      color: #d9d9d9;
    }
  }
}

@media (max-width: 580px) {
  .header-main {
    display: flex;
    
    &-nav {
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 1rem;
    }
  }
}
</style>