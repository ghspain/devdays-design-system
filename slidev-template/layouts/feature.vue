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

// Las rutas de /public del frontmatter deben llevar el base de despliegue
// (GitHub Pages: /<repo>/deck/); en dev el base es "/" y queda igual.
const image = computed(() => {
  const src = $frontmatter?.image
  if (!src) return null
  if (/^(https?:|data:|\/\/)/.test(src)) return src
  const base = import.meta.env.BASE_URL || '/'
  return base.replace(/\/$/, '') + '/' + String(src).replace(/^\//, '')
})
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
