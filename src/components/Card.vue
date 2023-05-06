<script setup>
const { image, firstName, family } = defineProps([
  "image",
  "firstName",
  "family",
]);
console.log("NAME:", firstName);
</script>

<template>
  <n-card>
    <template #cover>
      <img :src="image" />
    </template>
    <h3>{{ firstName }}</h3>
    <h5>{{ family }}</h5>
    <slot> </slot>
  </n-card>
</template>

<style scoped>
.n-card {
  width: 200px;
  margin: 10px 20px;
}

.n-card img {
  height: 250px;
}

p {
  font-size: 10px;
}

.jobs {
  display: flex;
  flex-wrap: wrap;
}
</style>