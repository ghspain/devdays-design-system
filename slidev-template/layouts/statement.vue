<template>
  <div class="slidev-layout statement text-center flex flex-col justify-center halo halo-green">
    <div class="z-10 px-16">
      <slot />
    </div>
  </div>
</template>

<style scoped>
:deep(h1) {
  font-size: 80px; /* hero 60pt */
  line-height: 1.05;
}
</style>
