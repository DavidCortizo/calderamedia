<template>
  <form id="newsLetterForm" class="form" action="" >
    <div class="form_fild">
      <label for="name" class="field_label">label</label>
      <input v-model="name" type="text" class="field_input" name="name">
    </div>
    {{ name }}
  </form>
</template>

<script>
export default {
  data() {
    return {
      errors: [],
      name: null,
      email: null
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

<style>
</style>
