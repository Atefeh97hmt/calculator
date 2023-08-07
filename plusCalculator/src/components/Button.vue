<template>
    <button @click="onClick">
      <slot></slot>
    </button>
  </template>
  
  <script setup>
  import { defineProps, defineEmits } from 'vue';
  
  const { emit } = defineEmits();
  
  const onClick = () => {
    // Emit the button label to the parent component (Calculator.vue)
    emit('click', props.children);
  };
  </script>