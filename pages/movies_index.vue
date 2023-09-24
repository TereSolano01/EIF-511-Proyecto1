<script>
  export default {
    async asyncData({ $content, params }) {
      const movies = await $content('movies').fetch()
      return {
        movies
      }
    }
  }
</script>

<template>
<div>
    <HeaderView />
    <h2 style="margin-top: 15px">Películas</h2>
    <p>Esta sección presenta información sobre películas.</p>
    <div class="container centered-content">
      <ul>
        <div class="grid-container">
          <li class="grid-item" v-for="movie of movies" :key="movie.slug">
              <img class="u-max-full-width" :src="'/images/'+movie.image" alt="Descripción de la imagen">
              <NuxtLink :to="{ name: 'movies-slug', params: { slug: movie.slug } }">{{movie.Título}}</NuxtLink>
              <p class="goto"><NuxtLink :to="{ name: 'movies-slug', params: { slug: movie.slug } }"> Ver película<i class="fa-solid fa-chevron-right" style="color: #000000;"></i></NuxtLink></p>
            </li>
        </div>
   </ul>
  </div>
   <FooterView />
 </div>
</template>

<style scoped>
@import url('../static/css/indexMovies.css');

.fila {
  display: flex;
}
</style>