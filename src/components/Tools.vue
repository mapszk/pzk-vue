<template>
  <div class="grid">
    <ToolsItem
      v-for="tool of tools"
      :key="tool.id"
      :img="tool.img"
      :name="tool.name"
    />
  </div>
</template>

<script>
import ToolsItem from '@/components/ToolsItem.vue'

export default {
  name: 'Tools',
  components: { ToolsItem },
  props: ['tools']
}
</script>

<style scoped>
.grid{
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(100px, 1fr));
  gap: 1rem;
  margin: 1rem 0px;
}
</style>
