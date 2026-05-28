<script setup lang="ts">
import { isDark } from '@slidev/client'
import { computed } from 'vue'

const label = computed(() => (isDark.value ? 'Bright room' : 'Dark room'))

function toggle() {
  isDark.value = !isDark.value
}
</script>

<template>
  <button
    class="brightness-toggle"
    type="button"
    :aria-pressed="isDark"
    :aria-label="`Switch to ${label.toLowerCase()} mode`"
    @click="toggle"
  >
    <span class="brightness-toggle__dot" />
    <span class="brightness-toggle__label">{{ label }}</span>
  </button>
</template>

<style scoped>
.brightness-toggle {
  position: fixed;
  top: 0.875rem;
  right: 0.875rem;
  z-index: 100;
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  padding: 0.35rem 0.7rem 0.35rem 0.55rem;
  border-radius: 9999px;
  background: rgba(255, 255, 255, 0.85);
  color: var(--rh-navy, #0B3D5C);
  font-family: 'IBM Plex Sans', system-ui, sans-serif;
  font-size: 0.72rem;
  font-weight: 500;
  letter-spacing: 0.02em;
  border: 1px solid rgba(11, 61, 92, 0.18);
  cursor: pointer;
  backdrop-filter: blur(10px);
  transition: background-color 120ms ease, color 120ms ease, border-color 120ms ease;
}
.brightness-toggle:hover {
  background: rgba(255, 255, 255, 1);
}
.brightness-toggle__dot {
  width: 0.55rem;
  height: 0.55rem;
  border-radius: 9999px;
  background: var(--rh-navy, #0B3D5C);
  box-shadow: 0 0 0 2px rgba(11, 61, 92, 0.12);
}
:global(.dark) .brightness-toggle {
  background: rgba(15, 23, 42, 0.8);
  color: #E2E8F0;
  border-color: rgba(226, 232, 240, 0.2);
}
:global(.dark) .brightness-toggle:hover {
  background: rgba(15, 23, 42, 1);
}
:global(.dark) .brightness-toggle__dot {
  background: #E2E8F0;
  box-shadow: 0 0 0 2px rgba(226, 232, 240, 0.18);
}
</style>
