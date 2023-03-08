<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <NoteCard/>
</template>

<script>
import NoteCard from './components/NoteCard.vue'

export default {
  name: 'App',
  components: {
    NoteCard
  }
}
</script>

<style scoped>
img{
  position: absolute;
  z-index: -1;
  max-width: 30vw;
  /* right: 50px; */
  /* height: auto; */
  opacity: 0.1;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  /* margin-top: 60px; */
}
</style>
