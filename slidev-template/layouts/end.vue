<template>
  <div class="slidev-layout end text-center flex flex-col items-center justify-center halo">
    <div class="z-10">
      <slot />
    </div>
    <div class="logos mono">
      <span class="accent-green">●</span>
      <span class="accent-purple">●</span>
      <span class="accent-lime">●</span>
    </div>
  </div>
</template>

<style scoped>
:deep(h1) {
  font-size: 88px;
  background: var(--grad-ai);
  -webkit-background-clip: text;
  background-clip: text;
  color: transparent;
}
:deep(p) {
  color: var(--c-text-muted);
}
.logos {
  position: absolute;
  bottom: 40px;
  left: 0;
  right: 0;
  font-size: 12px;
  letter-spacing: 8px;
}
</style>
