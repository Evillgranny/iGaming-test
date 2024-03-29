<script setup lang="ts">
import CardFront from '@/components/atoms/CardFront.vue'

defineProps<{
  isFlipped: boolean;
}>();
</script>

<template>
  <div :class="['card', { flipped: isFlipped }]">
    <div class="card-inner">
      <CardFront class="card-front" :number="12" suit="♣" />
      <div class="card-back"></div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.card {
  width: 175px;
  height: 286px;
  position: relative;

  @media screen and (max-width: 768px) {
    width: 20vw;
    height: calc(20vw * 1.6337);
  }
  @media (max-height: 10vh) {
    .card {
      height: 10vh;
      width: calc(10vh / 1.6337);
    }
  }

  &-inner {
    width: 100%;
    height: 100%;
    position: absolute;
    transform-style: preserve-3d;
    border-radius: 10%;
  }

  &-front,
  &-back {
    width: 100%;
    height: 100%;
    position: absolute;
    backface-visibility: hidden;
    border-radius: 10%;
    overflow: hidden;
  }

  &-front {
    transform: rotateY(180deg);
    width: 100%;
    height: 100%;
  }

  &-back {
    background: url("@/assets/images/card-back.webp") no-repeat center center / 100% 100%;
  }

  &-rank {
    font-size: 48px;
    color: #000000;
    font-weight: 600;
    margin-top: 10px;
    margin-left: 23px;
  }

  &-suit {
    font-size: 60px;
    color: #000000;
    font-weight: 600;
    margin-top: 2%;
    margin-left: 11.5%;
  }
}

@keyframes flip {
  from {
    z-index: 20;
  }
  35% {
    transform: scale(1.4) translateY(-100px);
  }
  to {
    transform: scale(1) rotateY(-180deg) translateY(-300px);
  }
}

@keyframes flip-mobile  {
  from {
    transform: rotateY(0deg) translateY(0);
  }
  35% {
    transform: scale(1.5) translateY(-10vh);
  }
  to {
    transform: scale(2) rotateY(-180deg) translateY(-23vh);
  }
}

.flipped .card-inner {
  animation: flip 1.3s normal forwards;
  z-index: 20;

  @media screen and (max-width: 768px) {
    animation: flip-mobile 1.3s normal forwards;
  }
}
</style>