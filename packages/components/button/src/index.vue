<script setup lang="ts" name="O-Button">
import type { SizeType } from '../../types'
interface IButtonProps {
  o?: string
  to?: string
  light?: boolean
  text?: boolean
  size?: SizeType
  disabled?: boolean
  loading?: boolean
}

const props = withDefaults(defineProps<IButtonProps>(), {
  size: 'md',
  o: 'primary',
})
const slots = useSlots()
const isDisabled = computed(() => props.loading || props.disabled)
const onlyIcon = computed(() => slots.icon && !slots.default)
</script>

<template>
  <component
    :is="to ? 'a' : 'button'"
    v-bind="to && { href: to }"
    :disabled="isDisabled"
    :aria-disabled="isDisabled"
    class="o-button-base"
    :class="[
      light ? 'o-button-light' : '',
      text ? 'o-button-text' : '',
      `o-button-${size}`,
      isDisabled ? 'o-disabled' : 'o-transition o-button-hover o-button-active',
      onlyIcon && 'aspect-square px-0',
    ]"
    :o="o"
  >
    <div v-if="loading" i-carbon-circle-dash animate-spin />
    <slot v-else name="icon" />
    <slot />
  </component>
</template>
