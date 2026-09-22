<template>
  <div class="slidev-layout cover text-center halo">
    <div class="my-auto z-10">
      <slot />
      <v-click v-if="$slots.second">
        <slot name="second" />
      </v-click>
    </div>
    <div
      v-if="title"
      class="absolute bottom-6 left-0 right-0 text-center text-sm"
      style="color: var(--c-text-muted)"
    >
      {{ title }}
    </div>
  </div>
</template>

<script setup>
import { computed } from 'vue'
import { useSlideContext } from '@slidev/client'

const { $slidev } = useSlideContext()
const title = computed(() => $slidev?.config?.title)
</script>

<style scoped>
:deep(h1) {
  font-size: 64px;
  background: var(--grad-ai);
  -webkit-background-clip: text;
  background-clip: text;
  color: transparent;
}
</style>
