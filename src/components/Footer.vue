<template>
  <footer>
    <div>
      <a href="https://github.com/mapszk" target="_blank" rel="noreferrer noopener">
        <img src="https://icongr.am/feather/github.svg?size=128&color=052b36" alt="Github">
      </a>
      <router-link to="/">
        <div id="ojoLogo"></div>
      </router-link>
      <a href="mailto:martinpilaszek@gmail.com">
        <img src="https://icongr.am/feather/mail.svg?size=128&color=052b36" alt="Email">
      </a>
    </div>
  </footer>
</template>

<script>
import Lottie from 'lottie-web'
export default {
  name: 'Footer',
  mounted () {
    const ojoDiv = document.getElementById('ojoLogo')
    Lottie.loadAnimation({
      container: ojoDiv,
      path: '/animations/ojo.json',
      renderer: 'svg',
      loop: true,
      autoplay: true
    })
  }
}
</script>

<style scoped>
footer{
  height: 50px;
  width: 95%;
  max-width: 960px;
  margin: 0 auto;
}
div{
  height: 100%;
  max-width: 200px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin: 0 auto;
}
img{
  height: 22px;
}
#ojoLogo{
  width: 40px;
  padding-bottom: 0.2rem;
}
</style>
