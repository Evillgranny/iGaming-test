<script setup lang="ts">
import { ref } from "vue";
import CardsRow from "@/components/organisms/CardsRow.vue";

const fakeCards = ref([
  { isOpened: false },
  { isOpened: false },
  { isOpened: false },
]);

const flipMiddleCard = () => {
  fakeCards.value[1].isOpened = true;
};

const reset = () => {
  fakeCards.value.forEach((card) => {
    card.isOpened = false;
  });
};
</script>

<template>
  <main>
    <CardsRow class="cards-row" :cards="fakeCards" />
    <div>
      <button class="button" @click="flipMiddleCard">Flip</button>
      <button class="button" @click="reset">Reset</button>
    </div>
  </main>
</template>

<style lang="scss">
main {
  padding-top: 400px;
  display: flex;
  flex-direction: column;

  @media (max-width: 768px) {
    padding-top: 0;
    height: 100vh;
    justify-content: space-between;
    overflow: hidden;
    flex-direction: column-reverse;
  }
}

.button {
  padding: 10px 20px;
  border: 2px solid #ffffff;
  color: #fff;
  background: rgba(0, 0, 0, 0.5);
  cursor: pointer;
}

.cards-row {
  @media screen and (max-width: 768px) {
    transform: translateY(30%);
  }
}
</style>
