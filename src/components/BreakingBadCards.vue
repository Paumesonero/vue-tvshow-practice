<script setup>
import axios from "axios";
import Card from "./Card.vue";

// there is no pagination in this api, to see go to leson number 73
const response = await axios.get(
  `https://thronesapi.com/api/v2/Characters?pageSize=10`
);
const characters = response.data;
console.log(characters);
</script>

<template>
  <div class="container">
    <div class="cards">
      <Card
        v-for="character in characters"
        :key="character.id"
        :image="character.imageUrl"
        :firstName="character.firstName"
        :family="character.family"
      >
        <div>
          <p>{{ character.title }}</p>
        </div>
      </Card>
    </div>
  </div>
</template>

<style scoped>
.container {
  background-color: rgb(27, 26, 26);
  padding: 30px;
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