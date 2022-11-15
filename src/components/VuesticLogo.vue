<template>
  <img class="sidebar-brand-full" src="https://i.postimg.cc/mgpRK2Bd/3.png" :height="height" />
  <defs>
    <linearGradient id="paint0_linear" x1="0" y1="56.1386" x2="357.64" y2="56.1386" gradientUnits="userSpaceOnUse">
      <stop :stop-color="colorsComputed.end" />
      <stop offset="1" :stop-color="colorsComputed.start" />
    </linearGradient>
  </defs>
</template>

<script setup lang="ts">
  import { computed } from 'vue'
  import { useColors } from 'vuestic-ui'
  const { getColor, shiftHSLAColor } = useColors()

  const props = withDefaults(
    defineProps<{
      height?: number | string
      color?: string
    }>(),
    {
      height: 56,
      color: 'primary',
    },
  )

  const colorsComputed = computed(() => {
    const color = getColor(props.color, 'primary')
    return { start: color, end: shiftHSLAColor(color, { l: -20 }) }
  })
</script>
