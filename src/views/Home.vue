<template>
  <section id="hero">
    <Button mt="2rem" color="primary" >Button</Button>
    <Button mt="2rem" link href="/contact" color="primary">Link local</Button>
    <Button link href="https://github.com" external color="primary">External link</Button>
  </section>
</template>

<script>
import Button from '../components/Button.vue'

export default {
  name: 'Home',
  components: { Button }
}
</script>

<style scoped>
</style>
