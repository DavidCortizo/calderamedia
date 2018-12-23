<template>
  <nav class="nav">
    <div class="nav_content_wrapper">
      <div class="nav_brand">
        <nuxt-link exact class="nav_brand_logo active-link--not" to="/">
          <img
            class="nav_brand_img"
            src="../static/logo/logo_calderamedia.svg"
            alt="Caldera Media logo"
          >
        </nuxt-link>
      </div>
      <div class="nav_title is-size-4 has-text-weight-bold">{{ title }}</div>
      <ul class="nav_menu is-hidden-touch">
        <li v-for="link in navItems" :key="link.title" class="nav_item">
          <nuxt-link :to="link.url" class="nav_link">{{ link.title }}</nuxt-link>
        </li>
      </ul>

      <div class="mobile_nav is-hidden-desktop">
        <div class="menu_icon" @click="toggleNav">
          <transition name="fade" >
            <div v-if="!visible" key="open" class="menu_icon--open"/>
            <div v-else key="close" class="menu_icon--closed"/>
          </transition>
        </div>
        <ul v-if="visible" class="nav_menu--mobile">
          <li v-for="link in navItems" :key="link.title" class="nav_item">
            <nuxt-link :to="link.url" class="nav_link">{{ link.title }}</nuxt-link>
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>

<script>
export default {
  data() {
    return {
      visible: false,
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
  },
  methods: {
    toggleNav() {
      this.visible = !this.visible
    }
  }
}
</script>


<style lang="scss" scoped>
/* scoped mixins */
@mixin menuBar($width: 40, $height: 5, $bg: $primary) {
  @include object($width, $height, $bg);
  background-image: $gradient;
  border-radius: $radius;
}

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

.mobile_nav {
  margin-left: auto;
  height: 100%;
  width: auto;
  display: flex;
  justify-content: center;
  align-items: center;
  .menu_icon {
    height: 100%;
    width: 40px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: flex-start;
    cursor: pointer;
  }
  .menu_icon--open {
    @include menuBar(25);
    position: relative;
    &::before {
      content: '';
      @include menuBar();
      position: absolute;
      top: -10px;
    }
    &::after {
      content: '';
      @include menuBar();
      position: absolute;
      bottom: -10px;
    }
  }
  .menu_icon--closed {
    @include menuBar(25, 5, transparent);
    background-image: none;
    position: relative;
    &::before {
      content: '';
      @include menuBar();
      position: absolute;
      top: 0;
      transform: rotate(-45deg);
    }
    &::after {
      content: '';
      @include menuBar();
      position: absolute;
      bottom: 0;
      transform: rotate(45deg);
    }
  }
  .nav_menu--mobile {
    display: none;
  }
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s ease-in-out;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}
</style>
