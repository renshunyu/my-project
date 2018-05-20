<template>
  <div id="app" class="apps" >
    <router-view/>
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style>
.apps {
  //font-family: 'Avenir', Helvetica, Arial, sans-serif;
  //-webkit-font-smoothing: antialiased;
  //-moz-osx-font-smoothing: grayscale;
  //text-align: center;
  //color: #2c3e50;
  //margin-top: 60px;
  //background: url('./assets/bg.jpg');
  width: 99.95%;
  height: 99.9%;
  position: absolute;
}
</style>
