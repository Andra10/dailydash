<template>
  <button
    :class="[
      $style.wrapper,
      $style[`wrapper--${size}`],
      $style[`wrapper--${priority}`],
      $props.class,
    ]"
  >
    <DynamicIcon :icon="icon" />
  </button>
</template>

<script lang="ts" setup>
import {defineProps} from 'vue';
import DynamicIcon from './DynamicIcon.vue';

interface Props {
  icon: string;
  size?: 's' | 'm' | 'l' | 'xl';
  priority?: 'primary' | 'secondary';
}

const props = withDefaults(defineProps<Props>(), {
  size: 'm',
  priority: 'primary',
});
</script>

<style lang="scss" module>
button.wrapper {
  @apply flex items-center justify-center;

  // Priority
  &--primary {
    @apply bg-main-green text-white;
  }

  &--secondary {
    @apply text-medium-grey;

    &:hover {
      @include theme(light) {
        @apply text-black text-opacity-60;
      }

      @include theme(dark) {
        @apply text-white text-opacity-60;
      }
    }
  }

  // Size
  &--s {
    @apply w-7 h-7;
  }

  &--m {
    @apply w-10 h-10;
  }

  &--l {
    @apply w-10 h-10;
  }

  &--xl {
    @apply w-12 h-12;
  }
}
</style>
