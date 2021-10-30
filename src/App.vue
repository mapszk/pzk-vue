<template>
  <Header/>
  <main>
    <transition name="slide" mode="out-in">
      <router-view/>
    </transition>
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
@import url('https://fonts.googleapis.com/css2?family=Epilogue:wght@200;400;600;800&display=swap');

*, *::after, *::before{
  box-sizing: border-box;
}
body{
  margin: 0;
  padding: 0;
  font-family: "Epilogue", sans-serif;
  background-color: #f0f0f0;
}
h1,h2,h3,h4,h5,h6, p{
  margin: 0;
  padding: 0;
  color: #052b36;
}
h1, h2, h3, h4, h5, h6{
  font-weight: 600;
}
p{
  line-height: 1.4rem;
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
  color: #052b36;
  font-family: "Epilogue", sans-serif;
}
button{
  font-family: "Epilogue", sans-serif;
}

/* route transition */
.slide-enter-active, .slide-leave-active{
  transition: opacity 1s ease, transform .6s ease;
}
.slide-enter-from, .slide-leave-to{
  opacity: 0;
  transform: translateY(-15%);
}
</style>
