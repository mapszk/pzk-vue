<template>
  <div class="project">
    <div class="img_container">
      <img :src="img" alt="Project image">
    </div>
    <div class="text">
      <h2 class="title">{{name}}</h2>
      <p class="desc">{{desc}}</p>
      <Button :full="!isLargerThan640" link external color="primary" :href="link">Visit</Button>
    </div>
  </div>
</template>

<script>
import Button from '@/components/Button.vue'

export default {
  name: 'Project',
  components: { Button },
  data () {
    return {
      width: window.innerWidth
    }
  },
  created () {
    window.addEventListener('resize', () => {
      this.width = window.innerWidth
    })
  },
  unmounted () {
    window.removeEventListener('resize', () => {
      this.width = window.innerWidth
    })
  },
  props: {
    name: {
      type: String,
      required: true
    },
    desc: {
      type: String,
      required: true
    },
    img: {
      type: String,
      required: true
    },
    link: {
      type: String,
      required: true
    }
  },
  computed: {
    isLargerThan640 () {
      if (this.width > 640) return true
      else return false
    }
  }
}
</script>

<style scoped>
.project{
  margin-bottom: 1rem;
}
.img_container {
  max-height: 250px;
  overflow: hidden;
  border-radius: 10px;
}
img{
  height: 100%;
  width: 100%;
  object-fit: cover;
  border-radius: 10px;
}
.title{
  margin: .5rem 0;
}
.desc{
  margin-bottom: .5rem;
}

@media screen and (min-width: 640px){
  .project{
    display: flex;
    min-width: 160px;
  }
  .img_container{
    flex: 1 0 280px;
    min-height: 160px;
    margin: 0 1rem 0 0;
    height: initial;
  }
  .text{
    display: flex;
    flex-direction: column;
    justify-content: space-between;
  }
}
</style>
