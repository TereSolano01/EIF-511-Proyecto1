<script>
  export default {
    async asyncData({ $content, params }) {
      const album = await $content('albums', params.slug).fetch()
      const compositor = await $content('compositors').where({ id: album.compositorId }).only(['name']).fetch()
      const movie = await $content('movies').where({ id: album.movieId }).only(['name']).fetch()
      return { album, compositor, movie }
    }
  }
</script>

<template>
    <div>
      <HeaderView />
      <div>
          <h4>{{album.title}}</h4>
          <div class="content-section">
            <div class="image-and-title">
              <div class="image-column">
                <img :src="'/images/'+album.image">
              </div>
              <div class="title-column">
                <div>
                  <p>Compositores: <NuxtLink :to="'/compositors/'+album.compositorId">{{album.compositor}}</NuxtLink></p>   
                    <p> Año staticacion: {{album.year}};</p>
                    <p>Generos: {{album.fields}}</p>
                    <p>Pelicula: <NuxtLink :to="'/movies/'+album.movieId">{{album.movie}}</NuxtLink></p> 
                </div>
                    <div class="info-section">
                        <pre></pre>
                        <nuxt-content :document="album" />
                    </div>
                 </div>
               </div>
              </div>
            <div>
          </div>
      </div>
      <FooterView />
    </div>
  </template>
  


<style scoped>
@import url('../../static/css/details.css');
</style>