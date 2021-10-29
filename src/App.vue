<template>
  <main>
    <Header/>
    <router-view/>
  </main>
</template>

<script>
import Header from '@/components/Header.vue'
export default {
  components: { Header }
}
</script>

<style>
*, *::after, *::before{
  box-sizing: border-box;
}
body{
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
}
a{
  text-decoration: none;

}
</style>
