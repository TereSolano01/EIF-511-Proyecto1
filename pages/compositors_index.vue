<script>
  export default {
    async asyncData({ $content, params }) {
      const compositors = await $content('compositors').fetch()
      return {
        compositors
      }
    }
  }
</script>

<template>
  <div>
      <HeaderView />
      <h2 style="margin-top: 15px">Compositores</h2>
      <p>Esta sección presenta información sobre compositores.</p>
      <div class="container centered-content">
        <ul>
          <div class="grid-container">
            <li class="grid-item" v-for="compositor of compositors" :key="compositor.slug">
                <img class="u-max-full-width" :src="'/images/'+compositor.image" alt="Descripción de la imagen">
                <NuxtLink :to="{ name: 'compositors-slug', params: { slug: compositor.slug } }">{{compositor.name}}</NuxtLink>
                <p class="goto"><NuxtLink :to="{ name: 'compositors-slug', params: { slug: compositor.slug } }"> Ver compositor<i class="fa-solid fa-chevron-right" style="color: #000000;"></i></NuxtLink></p>
              </li>
          </div>
     </ul>
    </div>
     <FooterView />
   </div>
  </template>

  <style scoped>
@import url('../static/css/indexCompositores.css');

.fila {
  display: flex;
}
</style>