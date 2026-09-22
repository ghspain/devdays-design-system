<template>
  <div class="slidev-layout roadmap">
    <slot />
    <div
      class="grid gap-6 mt-8"
      :style="{ gridTemplateColumns: `repeat(${steps.length || 1}, minmax(0, 1fr))` }"
    >
      <div v-for="(s, i) in steps" :key="s" v-click class="card step">
        <div class="num mono">{{ String(i + 1).padStart(2, '0') }}</div>
        <slot :name="s" />
      </div>
    </div>
  </div>
</template>

<script setup>
import { useSlots, computed } from 'vue'

const slots = useSlots()
const steps = computed(() =>
  ['second', 'third', 'fourth', 'fifth'].filter((s) => slots[s]),
)
</script>

<style scoped>
.step {
  min-height: 240px;
}
.num {
  font-size: 40px;
  font-weight: 700;
  color: var(--green);
  line-height: 1;
}
:deep(h2) {
  font-size: 24px;
  margin: 10px 0 8px;
}
:deep(p) {
  color: var(--c-text-muted);
  font-size: 16px;
}
</style>
