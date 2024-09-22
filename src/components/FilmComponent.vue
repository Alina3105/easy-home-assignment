<template>
  <div
    class="card"
    :style="{
      borderColor: props.borderColor,
      boxShadow: `0 10px 15px ${props.borderColor}`,
    }"
  >
    <img
      :src="`https://image.tmdb.org/t/p/w500/${props.poster}`"
      alt="Movie Poster"
    />
    <h2>{{ props.title }}</h2>
    <p>Release Date: {{ props.releaseDate }}</p>
  </div>
</template>

<script setup>
// eslint-disable-next-line no-undef
const props = defineProps({
  title: String,
  poster: String,
  releaseDate: String,
  borderColor: String,
});
</script>

<style scoped>
.card {
  width: 250px;
  height: 470px;
  margin: 25px;
  border: 3px solid;
  border-radius: 8px;
  overflow: hidden;
  display: flex;
  flex-direction: column;
}

.card img {
  width: 100%;
  height: 350px;
  object-fit: fill;
}
.card h2 {
  text-align: center;
  margin: 15px;
}
.card p {
  margin-top: auto;
  padding-left: 15px;
  margin-bottom: 10px;
}
</style>
