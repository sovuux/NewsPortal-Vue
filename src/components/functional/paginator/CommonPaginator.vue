<script setup lang="ts">
import { computed, ref } from 'vue'
import CommonButton from '../button/CommonButton.vue'

interface Props {
  totalPages: number
}

const props = withDefaults(defineProps<Props>(), {
  totalPages: 8
})

const currentPage = ref<number>(1)

function changePage(page: number) {
  if (page >= 1 && page <= props.totalPages) {
    currentPage.value = page
  }
}

const displayedPages = computed(() => {
  const pages: (number | string)[] = []
  const { totalPages } = props
  const current = currentPage.value

  if (totalPages <= 7) {
    for (let i = 1; i <= totalPages; i++) {
      pages.push(i)
    }
  } else {
    if (current <= 4) {
      pages.push(1, 2, 3, 4, '...', totalPages)
    } else if (current >= totalPages - 3) {
      pages.push(1, '...', totalPages - 3, totalPages - 2, totalPages - 1, totalPages)
    } else {
			pages.push(1, '...', current - 1, current, current + 1, '...', totalPages)
		}
  }

  return pages
})
</script>

<template>
  <div class="paginator">
    <CommonButton
      :is-active="currentPage > 1"
      label="‹"
      :class="['paginator-arrow', { active: currentPage > 1 }]"
      @click-action="changePage(currentPage - 1)"
    />
    <CommonButton
      v-for="(page, index) in displayedPages"
      :key="index"
      :is-active="page !== '...'"
      :label="page.toString()"
      :class="['paginator-page', { active: page === currentPage }]"
      @click-action="typeof page === 'number' && changePage(page)"
    />
    <CommonButton
      :is-active="currentPage < props.totalPages"
      label="›"
      :class="['paginator-arrow', { active: currentPage < props.totalPages }]"
      @click-action="changePage(currentPage + 1)"
    />
  </div>
</template>

<style scoped lang="scss">
.paginator {
  display: flex;
  align-items: center;
  gap: 10px;
  &-arrow {
		color: #c0c0c0;
    font-size: clamp(20px, 2vw, 40px);
    background-color: transparent;
		cursor: default;
		user-select: none;
		&.active {
      color: #428d26;
			cursor: pointer;
    }
  }
  &-page {
    color: #262626;
    font-size: clamp(10px, 2vw, 20px);
    border: 1px solid transparent;
    border-radius: 3px;
    padding: 5px 10px;
		user-select: none;
    &:hover {
      border: 1px solid #428d26;
    }
    &.active {
      background-color: #428d26;
      color: #ffff;
    }
  }
}
</style>
