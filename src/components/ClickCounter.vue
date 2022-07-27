<script setup>
import { ref, computed } from 'vue';

const emit = defineEmits(['update:modelValue']);

const props = defineProps({
  modelValue: {
    type: Number,
    required: true,
  },
  max: {
    type: Number,
    default: null,
  },
  min: {
    type: Number,
    default: null,
  },
  step: {
    type: Number,
    default: 1,
  },
  textIncrease: {
    type: String,
    default: '+',
  },
  textDecrease: {
    type: String,
    default: '-',
  },
  layoutVertical: {
    type: Boolean,
    default: false,
  },
});

const isMax = computed(() =>
  props.max === null ? false : props.modelValue === props.max
);

const isMin = computed(() =>
  props.min === null ? false : props.modelValue === props.min
);

const increase = () => {
  if (props.isMax) return;

  let newVal = props.modelValue + props.step;
  if (props.max !== null && newVal > props.max) {
    newVal = props.max;
  }

  emit('update:modelValue', newVal);
};

const decrease = () => {
  if (props.isMin) return;

  let newVal = props.modelValue - props.step;
  if (props.min !== null && newVal < props.min) {
    newVal = props.min;
  }

  emit('update:modelValue', newVal);
};
</script>

<template>
  <button @click="increase()" :disabled="isMax">{{ textIncrease }}</button>
  <template v-if="layoutVertical"><br /></template>
  <button @click="decrease()" :disabled="isMin">{{ textDecrease }}</button>
</template>

<style scoped>
button {
  min-width: 64px;
}
</style>
