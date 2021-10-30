<template>
  <div class="grid-item">
    <img :src="img" :alt="name">
    <h5>{{name}}</h5>
  </div>
</template>

<script>
export default {
  name: 'ToolsItem',
  props: {
    img: {
      type: String,
      required: true
    },
    name: {
      type: String,
      required: true
    }
  }
}
</script>

<style scoped>
.grid-item{
  min-width: 100px;
  min-height: 100px;
  background-color: white;
  padding: 1rem;
  border-radius: 10px;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  transition: transform 0.5s ease-in-out 0s, box-shadow 0.5s ease 0s;
}
.grid-item:hover{
  transform: scale(0.95);
  box-shadow: rgb(0 0 0 / 25%) 10px 10px 45px -19px;
}
.grid-item>img{
  width: 50%;
}
.grid-item>h5{
  margin-top: .7rem;
}
</style>
