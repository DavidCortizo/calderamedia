<template>
  <div class="layout">
    <Nav />
    <nuxt/>
    <Footer />
  </div>
</template>

<script>
import Nav from '~/components/Nav.vue'
import Footer from '~/components/Footer.vue'

export default {
  components: {
    Nav,
    Footer
  }
}
</script>

<style lang="scss">
html {
  font-family: $arsenal;
  font-size: 16px;
  word-spacing: 1px;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  box-sizing: border-box;
}
*,
*:before,
*:after {
  box-sizing: border-box;
  margin: 0;
}

body {
  background-color: $white;
}

.layout {
  display: flex;
  flex-direction: column;
}
</style>
