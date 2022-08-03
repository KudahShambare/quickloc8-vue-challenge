<template>
 <MyMessages/>
  <HomePage />
</template>

<script>
import HomePage from './components/HomePage.vue'
import MyMessages from './components/MyMessages.vue'

export default {
  name: 'App',
  components: {
    HomePage,
    MyMessages
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
