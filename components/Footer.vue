<template>
  <footer class="footer">
    <div class="footer_top">
      <a class="footer_prints footer_top_item is-italic is-size-4 has-text-centered">
        {{ print.body }}
        <span class="footer_prints_cta">
          {{ print.cta }}
        </span>
      </a>
      <div class="footer_social footer_top_item">
        <template v-for="icon in socialIcons">
          <a :href="icon.href" :key="icon.icon" target="_blank" class="footer_social_item" >
            <font-awesome-icon :icon="[icon.prefix, icon.icon]" class="icon"/>
          </a>
        </template>
      </div>
      <div class="footer_newsletter footer_top_item">
        <h3 class="newsletter_title is-size-5 is-italic has-text-weight-bold has-text-centered">
          Never miss new galleries
        </h3>
        <NewsLetterForm />
      </div>
    </div>
    <div class="footer_bottom footer_rights" >
      <span class="rights_copy">© 2018 Andres Caldera</span>
      <span class="rights_copy">-</span>
      <span class="rights_copy">All Rights Reserved</span>    
    </div>
  </footer>
</template>

<script>
import NewsLetterForm from './NewsLetterForm'
export default {
  components: {
    NewsLetterForm
  },
  data() {
    return {
      print: {
        body: 'For prints, projects or anything interesting,',
        cta: 'Get in touch with me!'
      },
      socialIcons: [
        {
          icon: 'instagram',
          prefix: 'fab',
          href: 'https://www.instagram.com/calderayes/'
        },
        {
          icon: 'twitter',
          prefix: 'fab',
          href: 'https://twitter.com/calderayes'
        },
        {
          icon: 'youtube',
          prefix: 'fab',
          href: 'https://www.youtube.com/channel/UCXX8XXDcpFDzuC7ECu3YDVw'
        },
        {
          icon: 'facebook',
          prefix: 'fab',
          href: 'https://www.facebook.com/andres.caldera.5'
        }
      ]
    }
  }
}
</script>

<style lang="scss" scoped>
footer {
  width: 100vw;
  border-top: 2px solid $black;
}
.footer_top {
  width: 100%;
  max-width: 1200px;
  height: auto;
  display: flex;
  align-items: center;
  justify-content: space-around;
  padding: 1rem;
  margin: 0 auto;
}
.footer_top_item {
  width: 33%;
}
.footer_prints {
  display: flex;
  flex-direction: column;
  color: $black;
  &:hover {
    .footer_prints_cta {
      color: $primary;
    }
  }
}
.footer_prints_cta {
  text-decoration: underline;
  transition: color 0.3s ease-in-out;
}
.footer_social {
  display: flex;
  justify-content: space-around;
}
.footer_social_item {
  color: $black;
  font-size: 2rem;
  .icon {
    color: $gradient;
  }
  &:hover {
    color: $primary;
    transition: color 0.3s ease-in-out;
  }
}
.newsletter_title {
  margin-bottom: 1rem;
}
.footer_bottom {
  background-color: $black;
  color: $white;
  height: 80px;
  display: flex;
  align-items: center;
  justify-content: center;
}
.rights_copy {
  margin: 0 0.5rem;
}
</style>
