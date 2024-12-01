<script setup lang="ts">
import DzenIcon from '@/assets/svg/icons/dzen.svg'
import CartIcon from '@/assets/svg/icons/shopping-cart.svg'
import StarIcon from '@/assets/svg/icons/star.svg'
import TelegramIcon from '@/assets/svg/icons/telegram.svg'
import VkIcon from '@/assets/svg/icons/vk.svg'
import YoutubeIcon from '@/assets/svg/icons/youtube.svg'
import CommonButton from '@/components/functional/button/CommonButton.vue'
import type { Link } from '@/types/LinkType'

const medias: Link[] = [
  {
    href: '#',
    content: TelegramIcon
  },
  {
    href: '#',
    content: DzenIcon
  },
  {
    href: '#',
    content: YoutubeIcon
  },
  {
    href: '#',
    content: VkIcon
  }
]

const navItems: Link[] = [
  {
    href: '/',
    content: 'Форум'
  },
  {
    href: '/',
    content: 'Поиск'
  },
  {
    href: '/',
    content: 'Контакты'
  }
]

const userItems: Link[] = [
  {
    href: '/',
    content: StarIcon
  },
  {
    href: '/',
    content: CartIcon
  }
]
</script>

<template>
  <div class="top-panel">
    <nav class="top-panel-media">
      <a v-for="media in medias" :key="media.href" class="top-panel-media-item" :href="media.href">
        <img :src="media.content" alt="img" class="top-panel-media-item-icon" />
      </a>
    </nav>
    <div class="top-panel-menu">
      <nav class="top-panel-menu-navbar">
        <RouterLink
          v-for="navItem in navItems"
          :key="navItem.href"
          :to="navItem.href"
          class="top-panel-menu-navbar-link"
        >
          {{ navItem.content }}
        </RouterLink>
      </nav>
      <nav class="top-panel-menu-user">
        <a v-for="userItem in userItems" :key="userItem.href" class="top-panel-menu-user-item">
          <img :src="userItem.content" alt="img" class="top-panel-menu-user-item-icon" />
        </a>
        <CommonButton :is-active="true" label="Личный кабинет" class="top-panel-button" />
      </nav>
    </div>
  </div>
</template>

<style scoped lang="scss">
.top-panel {
  user-select: none;
  background-color: #262626;
  display: flex;
  justify-content: space-between;
  align-items: center;
  color: #f3f3f3;
  height: 52px;
  padding: 0 5%;
  &-media {
    display: flex;
    align-items: center;
    gap: clamp(0.5rem, 2vw, 1.5rem);
    &-item {
      cursor: pointer;
      &-icon {
        width: clamp(12px, 2vw, 20px);
        height: auto;
      }
    }
  }
  &-menu {
    display: flex;
    align-items: center;
    gap: clamp(0.5rem, 2vw, 2rem);
    &-navbar {
      font-size: clamp(7px, 2vw, 15px);
      display: flex;
      align-items: center;
      gap: clamp(0.5rem, 2vw, 2rem);
      &-link {
        color: white;
        font-weight: bold;
        transition:
          color 0.3s ease,
          background-color 0.3s ease;
        &:hover {
          color: #d9d9d9;
        }
      }
    }
    &-user {
      display: flex;
      align-items: center;
      gap: clamp(0.5rem, 2vw, 2rem);
      &-item {
        &-icon {
          width: clamp(12px, 2vw, 24px);
          height: auto;
        }
      }
    }
  }
  &-button {
    background-color: #428d26;
    color: #ffff;
    border-radius: 3px;
    font-size: clamp(6px, 2vw, 14px);
    padding: clamp(4px, 1vw, 6px) clamp(8px, 2vw, 12px);
    transition:
      color 0.3s ease,
      background-color 0.3s ease;
    &:hover {
      background-color: #296313;
    }
  }
}
</style>