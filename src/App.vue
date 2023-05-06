<script setup>
import BreakingBadCardSuspense from "./components/BreakingBadCardSuspense.vue";
import RickMortyCards from "./components/RickMortyCards.vue";
import PracticeSlot from "./components/PracticeSlots.vue";
import TheHero from "./components/TheHero.vue";
import { ref } from "vue";

const isBreakingBad = ref(true);
</script>
<template>
  <main>
    <TheHero
      :isBreakingBad="isBreakingBad"
      @selectShow="isBreakingBad = !isBreakingBad"
    />
    <!-- This below will make that if we are in one of those components on page3 for example
     and swiped again we will go back to the first page -->

    <!-- <BreakingBadCardSuspense v-if="isBreakingBad" />
    <RickMortyCards v-else /> -->

    <!-- Instead we can do this: -->
    <KeepAlive>
      <Component
        :is="isBreakingBad ? BreakingBadCardSuspense : RickMortyCards"
      />
    </KeepAlive>

    <!-- <PracticeSlot>
      <h1>Slot</h1>
      <template #header>
        <div>
          <h2>Header here my friend</h2>
          <a href="">Page1</a>
          <a href="">Page2</a>
        </div>
      </template>
      <template #footer>
        <div>
          <ul>
            <li>Facebook</li>
            <li>Instagram</li>
            <li>Linkedin</li>
          </ul>
        </div>
      </template>
    </PracticeSlot> -->
  </main>
</template>
