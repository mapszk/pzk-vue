<template>
  <Header/>
  <main>
    <router-view/>
  </main>
  <Footer/>
</template>

<script>
import Header from '@/components/Header.vue'
import Footer from '@/components/Footer.vue'
export default {
  components: { Header, Footer }
}
</script>

<style>
*, *::after, *::before{
  box-sizing: border-box;
}
body{
  margin: 0;
  padding: 0;
  font-family: sans-serif;
  background-color: #f0f0f0;
}
h1,h2,h3,h4,h5,h6, p{
  margin: 0;
  padding: 0;
}
section{
  padding: 2.5rem 0;
}
main{
  width: 95%;
  max-width: 960px;
  margin: 0 auto;
  min-height: calc(100vh - 100px);
}
a{
  text-decoration: none;
}
</style>
