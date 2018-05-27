<template>
  <div class="dashboard">
    <div id="myChart" class="mychar" style="width: 100%; height: 100%;">
      <ditu></ditu>
    </div>
    <!--<div id="myChart1" class="mychar"><bingtu></bingtu></div>
    <div id="myChart2" class="mychar"><bingtu></bingtu></div>
    <div id="myChart3" class="mychar"><bingtu></bingtu></div>
    <div id="myChart4" class="mychar"><bingtu></bingtu></div>
    <div id="myChart5" class="mychar"><bingtu></bingtu></div>-->
  </div>
</template>
<script >
import ditu from './map/ditu'
// import bingtu from './bingtu/bingtu'
// import echarts from 'echarts'
export default {
  name: 'HelloWorld',
  components: {
    ditu
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
.dashboard {
  position: relative;
  width: 100%;
  height: 100%;
  margin: 0px;
  padding: 0px;
  padding-top: 0%;
  background: url('../assets/bg.jpg');
  background-size: 100% 100%;
}

.mychar {
  //background-color: #ff0000;
  width: 33%;
  height: 33%;
  border-width: 1px;
  float: left;
}
</style>
