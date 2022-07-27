<script setup>
import { ref, computed } from 'vue';
/*import HelloWorld from './components/HelloWorld.vue';
import ClickCounter from './components/ClickCounter.vue';

const m = computed(() => `Hello World ${clickCount.value}`);

const clickCount = ref(0);
const clickCount1 = ref(0);
*/

import ChristmasCalendar from './components/ChristmasCalendar.vue';
const windows = [
  {
    day: 1,
    bg: 'red',
    size: 2,
  },
  {
    day: 3,
    bg: 'blue',
    size: 3,
  },
  {
    day: 2,
    bg: 'green',
    size: 1,
  },
  {
    day: 4,
    bg: 'green',
    size: 2,
  },
  {
    day: 6,
    bg: 'green',
    size: 3,
  },
  {
    day: 5,
    bg: 'green',
    size: 1,
  },
  {
    day: 7,
    bg: 'green',
    size: 2,
  },
  {
    day: 9,
    bg: 'green',
    size: 2,
  },
  {
    day: 8,
    bg: 'green',
    size: 2,
  },
  {
    day: 0,
    bg: 'green',
    size: 2,
  },
];
</script>

<template>
  <ChristmasCalendar :windows="windows" />

  <!--
  <HelloWorld :msg="m" />
  <h1>{{ clickCount }}</h1>
  <ClickCounter
    v-model="clickCount"
    :max="10"
    :min="-1"
    :step="3"
    text-increase="+ 3"
    text-decrease="Sub 3"
  />
  <h1>{{ clickCount1 }}</h1>
  <ClickCounter v-model="clickCount1" :step="10" :layout-vertical="true" />

  -->
</template>

<style scoped></style>
