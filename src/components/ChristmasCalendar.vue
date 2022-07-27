<script setup>
import { ref, computed, onMounted } from 'vue';
import ChristmasCalendarWindow from './ChristmasCalendarWindow.vue';
const props = defineProps({
  windows: {
    type: Array,
  },
});

const second = ref(0);
const minute = ref(0);
const currentDay = ref(0);

const isActive = (day) => currentDay.value === day;

const clicked = (day) => {
  if (currentDay.value === day) {
    alert(day);
  }
};

const initTime = () => {
  const d = new Date();
  second.value = d.getSeconds();
  minute.value = d.getMinutes();
  currentDay.value = minute.value % 10;
};

onMounted(() => {
  initTime();
  document.addEventListener('visibilitychange', initTime);

  setInterval(() => {
    second.value === 59 ? (second.value = 0) : second.value++;
    if (second.value === 0) {
      minute.value++;
      currentDay.value = minute.value % 10;
    }
  }, 1000);
});
</script>

<template>
  {{ minute }} : {{ second }}

  <div class="christmas-calendar">
    <ChristmasCalendarWindow
      v-for="{ day, bg, size } in windows"
      :key="day"
      :day="day"
      :bg="bg"
      :size="size"
      :active="isActive(day)"
      @click="clicked(day)"
    />
  </div>
</template>

<style scoped>
.christmas-calendar {
  background-color: pink;
  display: grid;
  gap: 5px 10px;
  grid-template-columns: repeat(4, 1fr);
}
</style>
