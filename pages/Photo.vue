<template>
  <section class="photo" >
    <div class="item item1">Banner</div>
    <div class="item item2">High</div>
    <div class="item item3">Insta</div>
    <div class="item item4">Gallery</div>
  </section>
</template>

<script>
export default {}
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
  background-color: $primary;
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 1rem;
}
.item1 {
  grid-area: banner;
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
