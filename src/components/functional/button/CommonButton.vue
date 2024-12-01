<script setup lang="ts">
interface Props {
  label?: string
  subtitle?: string
  isActive: boolean
}

const emit = defineEmits(['click-action'])

const props = withDefaults(defineProps<Props>(), {
  label: 'button',
  isActive: true
})
</script>

<template>
  <button
    :class="{ 'button-disabled': !props.isActive }"
    class="button"
    @click="emit('click-action')"
  >
    <slot name="buttonIcon" />
    <div class="button-text">
      <span v-if="props.subtitle" class="button-text-subtitle">{{ props.subtitle }}</span>
      <span>{{ props.label }}</span>
    </div>
  </button>
</template>

<style scoped lang="scss">
.button {
  background-color: transparent;
  display: flex;
  gap: 0.5rem;
  border: none;
  color: black;
  padding: 14px 6px;
  cursor: pointer;
  &-text {
    display: flex;
    flex-direction: column;
    text-align: left;
    &-subtitle {
      font-size: clamp(7px, 2vw, 14px);
    }
  }
}
</style>
