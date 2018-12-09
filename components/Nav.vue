<template>
  <nav class="nav">
    <div class="nav_content_wrapper">
      <div class="nav_brand">
        <nuxt-link exact class="active-link--not" to="/">logo</nuxt-link>
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
.nav_brand_logo {
  background-color: transparent;
}
.nav_title {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
.nav_menu {
  display: flex;
  list-style: none;
  margin-left: auto;
}
.nav_item {
}
.nav_link {
  text-decoration: none;
  color: $black;
  padding: 0.8rem 0.5rem;
}
/* .exact-active-link {
  background-color: $primary;
} */
.active-link {
  background-color: $primary;
}
.active-link--not {
  background-color: transparent;
}
</style>
