<template>
  <div>
    <div v-if="isLoading">
      <MySpinner />
    </div>
    <div v-if="error" class="error">Ops...{{ error }}</div>
    <div v-if="!isLoading && !error">
      <div class="container">
        <FilmComponent
          FilmComponent
          v-for="(movie, index) in movies"
          :key="movie.id"
          :title="movie.title"
          :poster="movie.poster_path"
          :release-date="movie.release_date"
          :border-color="colors[index % colors.length]"
        />
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import FilmComponent from './FilmComponent.vue';
import MySpinner from '../assets/MySpinner.vue';

const movies = ref([]);
const isLoading = ref(true);
const error = ref(null);
const colors = ['red', 'orange', 'yellow', 'green', 'blue', 'indigo', 'violet'];

async function fetchData() {
  isLoading.value = true;
  error.value = null;

  try {
    const response = await fetch(
      'https://api.themoviedb.org/3/movie/popular?api_key=4170bf35f7a61b8012d65de6ad644b9b&page=1',
    );
    const data = await response.json();
    movies.value = data.results;
  } catch (err) {
    error.value = 'Error fetching movies.';
  } finally {
    isLoading.value = false;
  }
}
onMounted(fetchData);
</script>

<style scoped>
.container {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
  align-items: center;
}
.error {
  background: linear-gradient(45deg, yellow, red, green, violet);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  padding: 15px 20px;
  font-size: 50px;
  text-align: center;
  margin: 20px auto;
  width: 80%;
  max-width: 600px;
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>
