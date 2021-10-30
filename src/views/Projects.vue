<template>
  <div class="home">
    <Project
      v-for="proj in projects"
      :key="proj.id"
      :name="proj.title"
      :img="proj.img"
      :link="proj.link"
      :desc="proj.desc"
    />
  </div>
</template>

<script>
import Project from '@/components/Project.vue'
import { projects } from '@/projects.js'

export default {
  name: 'Projects',
  components: { Project },
  data () {
    return {
      projects: projects.sort((a, b) => b.id - a.id)
    }
  }
}
</script>
