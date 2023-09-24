<script>
  export default {
    async asyncData({ $content, params }) {
      const albums = await $content('albums').fetch()
      return {
        albums
      }
    }
  }
</script>

<template>
  <div>
      <HeaderView />
      <h2 style="margin-top: 15px">Álbumes</h2>
      <p>Esta sección te sumerge en el fascinante mundo de los álbumes, ofreciendo detalles y datos intrigantes sobre cada uno de ellos.</p>
      <div class="container centered-content">
        <ul>
          <div class="grid-container">
            <li class="grid-item" v-for="album of albums" :key="album.slug">
                <img class="u-max-full-width" :src="'/images/'+album.image" alt="Descripción de la imagen">
                <NuxtLink :to="{ name: 'albums-slug', params: { slug: album.slug } }">{{album.name}}</NuxtLink>
                <p class="goto"><NuxtLink :to="{ name: 'albums-slug', params: { slug: album.slug } }"> Ver album<i class="fa-solid fa-chevron-right" style="color: #000000;"></i></NuxtLink></p>
              </li>
          </div>
     </ul>
    </div>
     <FooterView />
   </div>
  </template>
<style scoped>
@import url('../static/css/index.css');

.fila {
  display: flex;
}
</style>
