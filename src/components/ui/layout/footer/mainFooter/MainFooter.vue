<script setup lang="ts">
import ComputerIcon from '@/assets/svg/icons/computer.svg'
import CommonButton from '@/components/functional/button/CommonButton.vue'
import type { Link } from '@/types/LinkType'
import { RouterLink } from 'vue-router'
import Logo from '../../../../../../public/logo/logo.svg'

const platformLinks: Link[] = [
  { href: '/none', content: 'ElcoreStore' },
  { href: '/none', content: 'ElcoreCloud' },
  { href: '/none', content: 'ElcoreIDE' }
]

const srcLinks: Link[] = [
  { href: '/none', content: 'Что такое ElcorePLC' },
  { href: '/none', content: 'Документация' },
  { href: '/none', content: 'Обучающие материалы' },
  { href: '/none', content: 'Примеры использования' },
  { href: '/none', content: 'База знаний' }
]

const contactLinks: Link[] = [
  { href: '/none', content: 'Контакты' },
  { href: '/none', content: 'Новости и статьи' },
  { href: '/none', content: 'Сообщество (Форум)' },
  { href: '/none', content: 'Тех поддержка' }
]
</script>

<template>
  <div class="main-footer">
    <div class="main-footer-section">
      <RouterLink class="main-footer-section-logo" to="/">
        <img :src="Logo" alt="Logo" class="main-footer-section-logo-icon" />
        <h1 class="main-footer-section-logo-text">ElcorePLC</h1>
      </RouterLink>
      <h2 class="main-footer-section-text">Платформа для автоматизации ваших процессов</h2>
      <CommonButton label="Desktop" subtitle='Скачать' :is-active="true" class="main-footer-section-button-desktop">
        <template #buttonIcon>
          <img :src="ComputerIcon" alt="computer" />
        </template>
      </CommonButton>
      <h2 class="main-footer-section-text">© ООО «НПО «Фарватер» 2024</h2>
    </div>
    <div class="main-footer-section">
      <h2 class="main-footer-section-title">Платформа</h2>
      <RouterLink
        v-for="(link, index) in platformLinks"
        :key="index"
        :to="link.href"
        class="main-footer-section-link"
      >
        {{ link.content }}
      </RouterLink>
    </div>
    <div class="main-footer-section">
      <h2 class="main-footer-section-title">Обучение и ресурсы</h2>
      <RouterLink
        v-for="(link, index) in srcLinks"
        :key="index"
        :to="link.href"
        class="main-footer-section-link"
      >
        {{ link.content }}
      </RouterLink>
    </div>
    <div class="main-footer-section">
      <CommonButton :is-active="true" label="Личный кабинет" class="main-footer-section-button-pa" />
      <RouterLink
        v-for="(link, index) in contactLinks"
        :key="index"
        :to="link.href"
        class="main-footer-section-link"
        >{{ link.content }}</RouterLink
      >
    </div>
  </div>
</template>

<style scoped lang="scss">
.main-footer {
  background-color: #101010;
  color: #ffff;
  display: flex;
  justify-content: space-between;
  padding: 1% 5%;
  &-section {
    display: flex;
    flex-direction: column;
    gap: 1rem;
    &-logo {
      color: #ffff;
      display: flex;
      align-items: center;
      gap: 1rem;
      &-text {
        font-weight: bolder;
      }
    }
		&-text {
			font-size: clamp(9px, 2vw, 18px);
			width: 75%;
		}
		&-title {
			font-size: clamp(12px, 2vw, 24px);
			font-weight: bolder;
			color: #6c6c6c;
			cursor: default;
		}
    &-link {
      color: #ffff;
			font-size: clamp(9px, 2vw, 18px);
			&:hover {
				color: #d9d9d9;
				transition: color 0.3s ease, background-color 0.3s ease;
			}
    }
    &-button {
			&-desktop {
				color: #ffff;
				border: 1px solid #5b5b5b;
				border-radius: 3px;
        width: 100%;
        max-width: 155px;
        padding: 4px;
				display: flex;
        justify-content: flex-start;
				align-items: center;
				font-size: clamp(9px, 2vw, 18px);
				font-weight: bold;
        transition: color 0.3s ease, background-color 0.3s ease;
        &:hover {
          color: #6c6c6c;
        }
			}
			&-pa {
        font-size: clamp(9px, 2vw, 18px);
				color: #ffff;
				padding: clamp(6.5px, 2vw, 13px) clamp(8.5px, 2vw, 17px);
				border: 1px solid #ffff;
				border-radius: 3px;
				transition: color 0.3s ease, background-color 0.3s ease;
				&:hover {
					color: #d9d9d9;
					border-color: #d9d9d9;
				}
			}
    }
  }
}

@media (max-width: 1050px) {
  .main-footer {
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: left;
    &-section {
      display: flex;
      justify-content: center;
      align-items: center;
      text-align: center;
      margin: 3%;
    }
  }
}
</style>