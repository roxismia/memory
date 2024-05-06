<template>
  <MyTest /> 
  <MyTest1/>
  <!-- <MyTest3/> -->
</template>

<script>
import MyTest from './components/MyTest.vue'
import MyTest1 from './components/MyTest1.vue'
// import MyTest3 from './components/MyTest3.vue';

export default {
  name: 'App',
  components: {
    MyTest,
    MyTest1,
    // MyTest3
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
