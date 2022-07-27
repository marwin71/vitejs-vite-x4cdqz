<script setup>
import { ref, computed } from 'vue';
const props = defineProps({
  day: {
    type: Number,
    required: true,
  },
  bg: {
    type: String,
    default: 'none',
  },
  size: {
    type: Number,
    default: 1,
  },
  active: {
    type: Boolean,
    default: false,
  },
});
</script>

<template>
  <div class="christmas-calendar-window" :class="{ active: active }">
    {{ day }}
  </div>
</template>

<style scoped>
.christmas-calendar-window {
  display: flex;
  align-items: center;
  justify-content: center;
}
.active {
  border: 1px solid #000;
}
.active:hover {
  cursor: pointer;
}
</style>
