<template>
  <nav class="nav">
    <div class="nav_content_wrapper">
      <div class="nav_brand">
        <nuxt-link exact class="nav_brand_logo active-link--not" to="/">
          <img class="nav_brand_img" src="../static/logo/logo_calderamedia.svg" alt="Caldera Media logo">
        </nuxt-link>
      </div>
      <div class="nav_title">{{ title }}</div>
      <ul class="nav_menu" >
        <li v-for="link in navItems" :key="link.title" class="nav_item" >
          <nuxt-link :to="link.url" class="nav_link">{{ link.title }}</nuxt-link>
        </li>
      </ul>
    </div>
  </nav>
</template>

<script>
export default {
  data() {
    return {
      title: '',
      navItems: [
        {
          title: 'Photo',
          url: '/photo'
        },
        {
          title: 'Galleries',
          url: '/gallery'
        },
        {
          title: 'Video',
          url: '/video'
        },
        {
          title: 'Contact',
          url: '/contact'
        }
      ]
    }
  },
  watch: {
    $route(to, from) {
      if (to.name === 'index') {
        this.title = ''
      } else {
        this.title = this.$route.name
      }
    }
  },
  created() {
    if (this.$route.name === 'index') {
      this.title = ''
    } else {
      this.title = this.$route.name
    }
  }
}
</script>


<style lang="scss" scoped>
.nav {
  height: 60px;
  position: relative;
  box-shadow: map-get($box-shadow, 1);
}
.nav_content_wrapper {
  display: flex;
  height: 100%;
  width: 95vw;
  max-width: 1200px;
  align-items: center;
  padding: 0 1rem;
  margin: 0 auto;
}
.nav_brand {
  height: 75%;

  .nav_brand_logo {
    height: 100%;
  }
  .nav_brand_img {
    background-color: transparent;
    width: 100%;
    height: 100%;
  }
}
.nav_title {
  position: absolute;
  font-family: $julius;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
.nav_menu {
  display: flex;
  list-style: none;
  margin-left: auto;

  .nav_item {
    padding: 0rem 0.5rem;
  }
  .nav_link {
    text-decoration: none;
    color: $black;
    position: relative;

    transform-origin: -20%;
    &::after {
      content: '';
      width: 0%;
      position: absolute;
      border-radius: 10px;
      height: 3px;
      bottom: -4px;
      left: -10%;
      background-color: transparent;
      transform-origin: -20%;
      transition: opacity0.3s ease-in-out, width 0.3s ease-in-out,
        height 0.1s ease-in-out, background-color 0.3s ease-in-out;
    }
    &:hover {
      &::after {
        content: '';
        width: 120%;
        position: absolute;
        border-radius: 10px;
        height: 3px;
        bottom: -4px;
        transform-origin: -20%;
        background-color: rgba($primary, 0.8);
        background-image: $gradient;
        opacity: 0.8;
      }
    }
  }
  /* Active */
  .active-link {
    &::after {
      content: '';
      width: 120%;
      position: absolute;
      border-radius: 10px;
      height: 3px;
      bottom: -4px;
      background-color: rgba($primary, 0.8);
      background-image: $gradient;
    }
  }
  .active-link--not {
    background-color: transparent;
  }
}
</style>
