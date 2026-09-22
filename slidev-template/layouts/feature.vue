<template>
  <!-- "Title and image stacked": título arriba, captura 4K a sangre bajo -->
  <div class="slidev-layout feature">
    <div class="content z-10">
      <slot />
    </div>
    <img
      v-if="image"
      :src="image"
      class="shot"
      alt=""
    />
  </div>
</template>

<script setup>
import { computed } from 'vue'
import { useSlideContext } from '@slidev/client'

const { $frontmatter } = useSlideContext()
const image = computed(() => $frontmatter?.image)
</script>

<style scoped>
.feature {
  display: flex;
  flex-direction: column;
  gap: 28px;
}
.shot {
  width: 100%;
  object-fit: cover;
  border-radius: 12px;
  box-shadow: 0 24px 80px rgba(94, 236, 131, 0.12);
  border: 1px solid #1b232b;
}
</style>
