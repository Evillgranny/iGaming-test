<script setup lang="ts">
defineProps<{
  number: number;
  suit: string;
}>();
</script>

<template>
  <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 175 286" style="background-color: white;">
    <text x="23" y="58" font-size="48px" fill="#000000" font-weight="600">{{number}}</text>
    <text x="23" y="120" font-size="60px" fill="#000000" font-weight="600">{{suit}}</text>
  </svg>
</template>