<script setup lang='ts'>
import type { News } from '@/types/NewsType'

interface Props extends News {}

const props = withDefaults(defineProps<Props>(), {
	image: '#',
	type: 'Новость',
	title: 'Заголовок',
	description: 'Описание'
})
</script>

<template>
	<div class='card'>
		<div class='card-image'>
			<img :src="props.image" alt="image">
		</div>
		<div class='card-info'>
			<span v-if="props.date">{{ props.date }}</span>
      <span v-if="props.date && props.type">/</span>
      <span>{{ props.type }}</span>
		</div>
		<div class='card-title'>
			<h2 class='card-title-text'>{{ props.title }}</h2>
		</div>
		<div class='card-description'>
			<p class='card-description-text'>
				{{ props.description }}
			</p>
		</div>
	</div>
</template>

<style scoped lang='scss'>
.card {
	display: flex;
	flex-direction: column;
	gap: 1rem;
	width: 100%;
	max-width: 408px;
	height: auto;
	aspect-ratio: 408 / 426;
	cursor: pointer;
	&-image {
		background-color: #D9D9D9;
		display: flex;
		align-items: center;
		justify-content: center;
		width: 100%;
		height: 100%;
		max-height: 220px;
		border-radius: 6px;
	}
	&-info {
		font-size: clamp(7px, 2vw, 14px);
		color: #6C6C6C;
		display: flex;
		gap: 0.625rem;
	}
	&-title {
		&-text {
			font-size: clamp(12px, 2vw, 24px);
			font-weight: bolder;
			color: #262626;
		}
	}
	&-description {
		font-size: clamp(8px, 2vw, 16px);
		color: #262626;
	}
}
</style>