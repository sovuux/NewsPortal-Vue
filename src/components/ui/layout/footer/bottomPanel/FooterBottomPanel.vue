<script setup lang='ts'>
import DzenIcon from '@/assets/svg/icons/dzen.svg'
import TelegramIcon from '@/assets/svg/icons/telegram.svg'
import VkIcon from '@/assets/svg/icons/vk.svg'
import YoutubeIcon from '@/assets/svg/icons/youtube.svg'
import type { Link } from '@/types/LinkType'
import { RouterLink } from 'vue-router'

const mediaLinks: Link[] = [
	{ href: '#', content: TelegramIcon },
	{ href: '#', content: DzenIcon },
	{ href: '#', content: YoutubeIcon },
	{ href: '#', content: VkIcon }
]
</script>

<template>
	<div class='bottom-panel'>
		<nav class='bottom-panel-left'>
			<RouterLink v-for='(link, index) in mediaLinks' :key='index' :to='link.href'>
				<img :src="link.content" alt="media" class='bottom-panel-left-icon'>
			</RouterLink>
		</nav>
		<nav class='bottom-panel-right'>
			<RouterLink to='#' class='bottom-panel-right-link'>Политика конфиденциальности</RouterLink>
			<RouterLink to='#' class='bottom-panel-right-link'>Карта сайта</RouterLink>
		</nav>
	</div>
</template>

<style scoped lang="scss">
.bottom-panel {
	background-color: #262626;
	padding: 1% 5%;
	display: flex;
	justify-content: space-between;
	&-left {
		display: flex;
		gap: 1rem;
		&-icon {
			width: clamp(12px, 2vw, 20px);
			height: auto;
		}
	}
	&-right {
		display: flex;
		gap: 1rem;
		&-link {
			color: #ababab;
			font-size: clamp(8px, 2vw, 16px);
			transition: color 0.3s ease, background-color 0.3s ease;
			&:hover {
				color: #6c6c6c;
			}
		}
	}
}
</style>