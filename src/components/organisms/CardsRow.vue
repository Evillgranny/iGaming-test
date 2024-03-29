<script lang="ts" setup>
import BaseCard from '@/components/molecules/BaseCard.vue'

defineProps<{
  cards: {
    isOpened: boolean;
  }[];
}>();
</script>

<template>
  <div class="cards-row">
    <BaseCard
        v-for="(card, index) in cards"
        :key="`card-${index}`"
        :isFlipped="index === 1 ? card.isOpened : false"
        class="card"
    />
  </div>
</template>

<style lang="scss" scoped>
.cards-row {
  gap: 20px;
  margin: 0 auto;
  display: flex;
  justify-content: center;
}

.card {
  flex-shrink: 0;
}
</style>