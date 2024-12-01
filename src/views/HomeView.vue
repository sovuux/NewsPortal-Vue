<script setup lang="ts">
import NewsCard from '@/components/functional/cards/newsCard/NewsCard.vue'
import CommonPaginator from '@/components/functional/paginator/CommonPaginator.vue'
import { newsData } from '@/data/NewsData'
import type { Link } from '@/types/LinkType'
import type { News } from '@/types/NewsType'
import { onMounted, ref } from 'vue'
import { RouterLink } from 'vue-router'

interface LinkButton extends Link {
  isActive: boolean
}

const tagsButtons: LinkButton[] = [
  { href: '/', content: 'Все новости и статьи', isActive: true },
  { href: '/none', content: 'Новости', isActive: false },
  { href: '/none', content: 'Статьи', isActive: false }
]

const data = ref<News[]>([])

onMounted(() => {
  data.value = newsData
})
</script>

<template>
  <main class="main">
    <section class="main-section-title">
      <h1 class="main-section-title-text">Новости и статьи</h1>
    </section>
    <section class="main-section-tags">
      <RouterLink
        v-for="(tagButton, index) in tagsButtons"
        :key="index"
        class="main-section-tags-link"
        :to="tagButton.href"
      >
        {{ tagButton.content }}
      </RouterLink>
    </section>
    <section class="main-section-news">
      <NewsCard
        v-for="(item, index) in data"
        :key="index"
        :image="item.image"
        :date="item.date"
        :type="item.type"
        :title="item.title"
        :description="item.description"
      />
    </section>
    <section class='main-section-paginator'>
      <CommonPaginator :total-pages='11' />
    </section>
  </main>
</template>

<style scoped lang="scss">
.main {
  padding: 5% 5%;
  &-section {
    &-title {
      display: flex;
      justify-content: center;
      font-size: clamp(18px, 2vw, 36px);
      color: #262626;
      &-text {
        font-weight: bolder;
      }
    }
    &-tags {
      display: flex;
      align-items: center;
      gap: clamp(0.5rem, 2vw, 1rem);
      padding: 5% 0;
      &-link {
        border-radius: 20px;
        font-size: clamp(7px, 2vw, 14px);
        background-color: transparent;
        color: #428d26;
        border: 1px solid #428d26;
        padding: clamp(4px, 1vw, 6px) clamp(10px, 2vw, 14px);
        transition:
          color 0.3s ease,
          background-color 0.3s ease;
        &-hover {
          border-color: #296313;
          color: #296313;
        }
      }
    }
    &-news {
      display: flex;
      flex-wrap: wrap;
      gap: 1.5rem;
    }
    &-paginator {
      display: flex;
      justify-content: center;
    }
  }
}
.router-active-link {
  background-color: #428d26;
  border: 1px;
  color: #ffffff !important;
  &:hover {
    background-color: #296313;
  }
}

@media (max-width: 1893px) {
  .main-section-news {
    display: flex;
    justify-content: center;
  }
}
</style>
