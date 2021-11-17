<template>
  <form @submit.prevent="validation">
    <h2>Contact</h2>
    <label for="name">Name</label>
    <input v-model="name" type="text" id="name" name="name">
    <label for="email">Email</label>
    <input v-model="email" type="text" id="email" name="email">
    <label for="message">Message</label>
    <textarea v-model="message" name="message" id="message" cols="30" rows="10"></textarea>
    <Button type="submit" mt="1rem" color="secondary" :full="true">Send</Button>
    <transition name="slide">
      <span v-if="alert" :class="alertStyles">{{alertMsg}}</span>
    </transition>
  </form>
</template>

<script>
import Button from '@/components/Button.vue'

const emailRegex = /^[a-zA-Z0-9_.+-]+@[a-zA-Z0-9-]+\.[a-zA-Z0-9-.]+$/g
const endpoint = 'https://formspree.io/f/xdoyegpk'

export default {
  name: 'ContactForm',
  components: { Button },
  data () {
    return {
      name: '',
      email: '',
      message: '',
      alert: false,
      alertType: '',
      alertMsg: '',
      loading: false
    }
  },
  computed: {
    alertStyles () {
      return {
        error: this.alertType === 'error',
        success: this.alertType === 'success'
      }
    }
  },
  methods: {
    clearAlert () {
      setTimeout(() => {
        this.alert = false
        this.alertType = ''
        this.alertMsg = ''
      }, 5000)
    },
    async submit () {
      this.loading = true
      await fetch(endpoint, {
        method: 'POST',
        body: JSON.stringify({ name: this.name, email: this.email, message: this.message }),
        headers: {
          Accept: 'application/json'
        }
      })
        .then(() => {
          this.alert = true
          this.alertType = 'success'
          this.alertMsg = 'Sent! Thank you'
        })
        .catch(() => {
          this.alert = true
          this.alertType = 'error'
          this.alertMsg = 'An error has ocurred, please try again'
        })
        .finally(() => {
          this.loading = false
          this.clearAlert()
        })
    },
    validation () {
      if (!this.email | !this.name | !this.message) {
        this.alert = true
        this.alertType = 'error'
        this.alertMsg = 'Please fill all the fields'
        return this.clearAlert()
      } else if (!emailRegex.test(this.email)) {
        this.alert = true
        this.alertType = 'error'
        this.alertMsg = 'Please put a valid email'
        return this.clearAlert()
      } else {
        this.submit()
      }
    }
  }
}
</script>

<style scoped>
h2{
  color: #c8ff30;
  margin-bottom: .5rem;
}
label{
  display: block;
  margin-bottom: .3rem;
  color: #c8ff30;
}
input, textarea{
  display: block;
  width: 100%;
  height: 2.5rem;
  border-radius: 2rem;
  border: none;
  padding: 0 1rem;
  margin-bottom: .6rem;
}
input:focus, textarea:focus{
  border: 2px solid #c8ff30;
  outline: none;
}
textarea{
  border-radius: 1rem;
  height: 10rem;
  resize: none;
  padding: .8rem;
}
form{
  background-color: #052b36;
  padding: 1rem;
  border-radius: 1rem;
  position: relative;
}

/* alert */
span{
  font-weight: 600;
  position: absolute;
  text-align: center;
  padding: .75rem;
  left: 0;
  right: 0;
  margin-top: 1.5rem;
  border-radius: 2rem;
  display: block;
}
.error {
  background-color: red;
  color: white;
}
.success {
  background-color: #c8ff30;
  color: #052b36;
}
.slide-enter-active, .slide-leave-active {
  transition: opacity 1s, transform .5s;
}
.slide-enter, .slide-leave-to {
  opacity: 0;
  transform: translateY(10px)
}
</style>
