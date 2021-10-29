<template>
  <div class="menu" :class="{menuOn: menu, menuOff: !menu}">
    <button @click="menuOff" class="menu_off">
      <img src="https://icongr.am/feather/x.svg?size=128&color=052b36" alt="Close menu">
    </button>
    <router-link to="/">Home</router-link>
    <router-link to="/projects">Projects</router-link>
    <router-link to="/contact">Contact</router-link>
  </div>
  <header>
    <div class="navbar_container">
      <router-link to="/">
        <img class="logo" src="/images/logo-azul.svg" alt="PZK Logo">
      </router-link>
      <nav>
        <router-link to="/">Home</router-link>
        <router-link to="/projects">Projects</router-link>
        <router-link to="/contact">Contact</router-link>
      </nav>
      <button @click="menuOn" class="menu_on">
        <img src="https://icongr.am/feather/menu.svg?size=128&color=052b36" alt="Menu">
      </button>
    </div>
  </header>
</template>

<script>
export default {
  name: 'Header',
  data () {
    return {
      menu: false,
      test: false
    }
  },
  methods: {
    menuOn () {
      document.body.style.overflow = 'hidden'
      this.menu = !this.menu
    },
    menuOff () {
      document.body.style.overflow = 'auto'
      this.menu = !this.menu
    }
  }
}
</script>

<style scoped>
header{
  height: 50px;
  width: 95%;
  max-width: 960px;
  margin: 0 auto;
}
header>div{
  height: 100%;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
button>img{
  height: 22px;
}
.menu_on{
  background-color: transparent;
  border: none;
  cursor: pointer;
  padding: 0;
}
.logo{
  width: 75px;
}
nav{
  display: none;
}
nav>:not(:nth-child(1)){
  margin-left: 2rem;
}

@media screen and (min-width: 720px){
  .menu_on{
    display: none;
  }
  nav{
    display: block;
  }
}

.menu{
  background-color: white;
  height: 100vh;
  width: 100vw;
}
.menuOn{
  background-color: white;
  height: 100vh;
  width: 100vw;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  position: fixed;
  z-index: 99;
  transition: transform 1s ease;
}
.menu>:not(:first-child), .menu>:not(:last-child){
  margin-bottom: 2rem;
}
.menuOff{
  position: fixed;
  height: 100vh;
  width: 100vw;
  z-index: 99;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  transform: translateX(1000%);
  transition: transform 2s ease;
}
.menu>:not(:first-child){
  display: inline;
}
.menu_off{
  background: none;
  border: none;
  padding: 0;
  position: absolute;
  top: 1rem;
  right: 2rem;
}

</style>
