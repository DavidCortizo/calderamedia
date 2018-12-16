<template>
  <section class="photo" >
    
    <Banner class="item"/>
    <div class="item item2">High</div>
    <div class="item item3">Insta</div>
    <div class="item item4">
      Gallery
      <button class="button is-primary has-gradient">
        See galleries
      </button>
    </div>
  </section>
</template>

<script>
import Banner from '../components/Banner.vue'
export default {
  components: {
    Banner
  }
}
</script>

<style lang="scss" scoped>
.photo {
  height: 100%;
  width: 95vw;
  max-width: 1200px;
  margin: 2rem auto;
  display: grid;
  grid-template-columns: 2fr 1fr;
  grid-template-areas:
    'banner banner'
    'high insta'
    'gallery gallery';
}
.item {
  height: 300px;
  background-color: darken($white, 3);
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 1rem;
}
.item2 {
  grid-area: high;
}
.item3 {
  grid-area: insta;
}
.item4 {
  grid-area: gallery;
}
</style>
