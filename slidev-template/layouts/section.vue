<template>
  <div class="slidev-layout text-center flex flex-col items-center justify-center">
    <div class="bar" />
    <div class="z-10">
      <slot />
    </div>
  </div>
</template>

<style scoped>
.bar {
  width: 72px;
  height: 6px;
  border-radius: 999px;
  background: var(--grad-green);
  margin-bottom: 28px;
}
:deep(h1) {
  font-size: 60px;
}
:deep(h1::after) {
  content: '';
}
</style>
