<template>
  <div class="contact">
    <div class="form">
      <ContactForm/>
    </div>
    <div class="about">
      <h2>About me</h2>
      <p>
        My name is Martin, I develop websites adapted to the client needs, looking always for optimal performance, and using design standards according to the product or the service. I'm a self-taught person in constant learning. Let's work together!
      </p>
      <h2>Tools</h2>
      <h3>Development</h3>
      <Tools :tools="devTools" />
      <h3>Design</h3>
      <Tools :tools="designTools" />
    </div>
  </div>
</template>

<script>
import ContactForm from '@/components/ContactForm.vue'
import Tools from '@/components/Tools.vue'
import { tools } from '@/tools.js'

export default {
  name: 'Contact',
  components: { ContactForm, Tools },
  data () {
    return {
      devTools: tools.dev,
      designTools: tools.design
    }
  }
}
</script>

<style scoped>
.form{
  margin-bottom: 1rem;
}
h2{
  margin-bottom: .3rem;
}
p{
  margin-bottom: .8rem;
}

@media screen and (min-width: 720px){
  .contact{
    display: flex;
    justify-content: space-between;
  }
  .about{
    width: 50%;
  }
  .form{
    margin-bottom: 0;
    width: 45%;
    order: 1;
    align-self: flex-start;
  }
}
</style>
