<template>
  <form @submit.prevent="submit">
    <h2>Contact</h2>
    <label for="name">Name</label>
    <input v-model="name" type="text" id="name" name="name" />
    <label for="email">Email</label>
    <input v-model="email" type="text" id="email" name="email" />
    <label for="message">Message</label>
    <textarea
      v-model="msg"
      name="message"
      id="message"
      cols="30"
      rows="10"
    ></textarea>
    <Button type="submit" mt="1rem" color="secondary" :full="true">Send</Button>
    <span :class="alertStyles">{{ alertMsg }}</span>
  </form>
</template>

<script>
import Button from '@/components/Button.vue'
import { ref, computed } from 'vue'

const emailRegex = /^[a-zA-Z0-9_.+-]+@[a-zA-Z0-9-]+\.[a-zA-Z0-9-.]+$/g
const endpoint = 'https://formspree.io/f/xdoyegpk'

export default {
  name: 'ContactForm',
  components: { Button },
  setup () {
    const name = ref('')
    const email = ref('')
    const msg = ref('')
    const loading = ref(false)
    const alert = ref(false)
    const alertMsg = ref({})
    const alertStyles = computed(() => {
      return {
        visible: alert.value,
        error: alertMsg.value.type === 'error',
        success: alertMsg.value.type === 'success'
      }
    })
    const clearAlert = () => {
      setTimeout(() => {
        alert.value = false
        alertMsg.value = {}
      }, 5000)
    }
    const submit = async () => {
      loading.value = true
      await fetch(endpoint, {
        method: 'POST',
        body: JSON.stringify({
          name: this.name,
          email: this.email,
          message: this.message
        }),
        headers: {
          Accept: 'application/json'
        }
      })
        .then(() => {
          alert.value = true
          alertMsg.value = { type: 'success', msg: 'Sent! Thank you' }
        })
        .catch(() => {
          alert.value = true
          alertMsg.value = { type: 'error', msg: 'An error has ocurred, please try again' }
        })
        .finally(() => {
          loading.value = false
          clearAlert()
        })
    }
    const validation = () => {
      if (!email.value | !name.value | !msg.value) {
        alert.value = true
        alertMsg.value = { type: 'error', msg: 'Please fill all the fields' }
        return clearAlert()
      } else if (!emailRegex.test(this.email)) {
        alert.value = true
        alertMsg.value = { type: 'error', msg: 'Please put a valid email' }
        return clearAlert()
      } else {
        submit()
      }
    }

    return {
      name,
      email,
      msg,
      validation,
      loading,
      alertStyles
    }
  }
}
</script>

<style scoped>
h2 {
  color: #c8ff30;
  margin-bottom: 0.5rem;
}
label {
  display: block;
  margin-bottom: 0.3rem;
  color: #c8ff30;
}
input,
textarea {
  display: block;
  width: 100%;
  height: 2.5rem;
  border-radius: 2rem;
  border: none;
  padding: 0 1rem;
  margin-bottom: 0.6rem;
}
input:focus,
textarea:focus {
  border: 2px solid #c8ff30;
  outline: none;
}
textarea {
  border-radius: 1rem;
  height: 10rem;
  resize: none;
  padding: 0.8rem;
}
form {
  background-color: #052b36;
  padding: 1rem;
  border-radius: 1rem;
  position: relative;
}

/* alert */
span {
  font-weight: 600;
  position: absolute;
  text-align: center;
  padding: 0.75rem;
  left: 0;
  right: 0;
  margin-top: 1.5rem;
  border-radius: 2rem;
  display: block;
  transition: transform 1s ease, opacity 1s ease;
  transform: translateY(20px);
  opacity: 0;
}
.visible {
  transform: translateY(0);
  opacity: 1;
}
.error {
  background-color: red;
  color: white;
}
.success {
  background-color: #c8ff30;
  color: #052b36;
}
</style>
