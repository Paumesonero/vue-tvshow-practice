<script setup>
import axios from "axios";
import Card from "./Card.vue";
import {
  onMounted,
  onUpdated,
  onUnmounted,
  onBeforeMount,
  ref,
  watch,
} from "vue";

const characters = ref(null);
const page = ref(1);

onMounted(async () => {
  const res = await axios.get("https://rickandmortyapi.com/api/character");
  characters.value = res.data.results;
  console.log("this are values", characters.value);
});
watch(page, async () => {
  const response = await axios.get(
    `https://rickandmortyapi.com/api/character/?page=${page.value}`
  );
  characters.value = response.data.results;
});

// const state = ref(0);
// // life cicle hooks (similar to animations)
// onBeforeMount(() => {
//   console.log("ready to be mounted");
// });
// onMounted(() => {
//   console.log("mounted");
// });

// onUpdated(() => {
//   console.log("updated");
// });
// onUnmounted(() => {
//   console.log("component removed");
// });
</script>
<template>
  <div class="container">
    <div v-if="characters" class="cards">
      <Card
        v-for="character in characters"
        :key="character.id"
        :image="character.image"
        :firstName="character.name"
        :family="character.species"
      >
        <p>{{ character.status }}</p>
      </Card>
    </div>
    <div v-else>
      <n-spin size="large" class="cards spinner" />
    </div>
    <div class="button-container">
      <button @click="page--">-</button>
      <button @click="page++">+</button>
    </div>
  </div>
</template>
<style scoped>
.container {
  background-color: rgb(27, 26, 26);
  padding: 30px;
  margin-top: 30px;
}

.cards {
  max-width: 1000px;
  margin: 0 auto;
  display: flex;
  flex-wrap: wrap;
}

.cards h3 {
  font-weight: bold;
}

.cards p {
  font-size: 10px;
}

.jobs {
  display: flex;
  flex-wrap: wrap;
}

.button-container {
  display: flex;
  justify-content: center;
  padding-top: 30px;
}

.button-container button {
  border: none;
  width: 50px;
  height: 50px;
  border-radius: 100%;
  margin: 0 5px;
  cursor: pointer;
}

.spinner {
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>
