<template>
  <form id="newsLetterForm" class="form" action="" >

    <div class="field">
      <label for="name" class="label"> {{ nameLabel }} </label>
      <div class="control has-icons-left">
        <input v-model="name" class="input is-primary" type="text" placeholder="Name" name="name">
        <span class="icon is-small is-left is-flex u_j-c-c u_a-i-c">
          <font-awesome-icon :icon="['fas', 'user']" />
        </span>
      </div>
    </div>

    <div class="field">
      <label for="email" class="label"> {{ emailLabel }} </label>
      <div class="control has-icons-left">
        <input v-model="name" class="input is-primary" type="email" placeholder="Email" name="email">
        <span class="icon is-small is-left is-flex u_j-c-c u_a-i-c">
          <font-awesome-icon :icon="['fas', 'envelope']" />
        </span>
      </div>
    </div>
    {{ name }}
    <button class="button is-primary has-gradient">
      {{ sumbitLabel }}
    </button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      errors: [],
      name: null,
      email: null,
      nameLabel: 'Name',
      emailLabel: 'Email',
      sumbitLabel: 'Subscribe to newsletter'
    }
  },
  methods: {
    checkForm: function(e) {
      this.errors = []

      if (!this.name) {
        this.errors.push('Name required.')
      }
      if (!this.email) {
        this.errors.push('Email required.')
      } else if (!this.validEmail(this.email)) {
        this.errors.push('Valid email required.')
      }

      if (!this.errors.length) {
        return true
      }

      e.preventDefault()
    },
    validEmail: function(email) {
      var re = /^(([^<>()\[\]\\.,;:\s@"]+(\.[^<>()\[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/
      return re.test(email)
    }
  }
}
</script>

<style lang="scss" scoped>
.label {
  display: none;
}
</style>
