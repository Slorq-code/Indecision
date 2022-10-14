
<template>
  <image src="./assets/logo.png" />
  <MyIndecision/>
</template>


<script>
  import MyIndecision from "./components/MyIndecision.vue"

  export default {
    name: 'App',
    components: {
      MyIndecision
    }
  }
</script>


<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
