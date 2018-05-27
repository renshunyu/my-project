<template>
  <div id="mp" class="mmap">
      <quanguo id="chartmap" style="width: 39.6%; height: 65%; float: left;"></quanguo>
      <onlineusers id="liveacct" style="width: 26.4%; height: 65%; float: left;"></onlineusers>
      <bingtu id="bingtu1" style="width: 33%; height: 33%; float: left;"></bingtu>
      <zhutu id="zhutu2" style="width: 33%; height: 33%; float: left;"></zhutu>
      <szhutu id="szhutu3" style="width: 33%; height: 33%; float: left;"></szhutu>
      <taskcyclenum id="taskcyclenum" style="width: 16.5%; height: 33%; float: left;"></taskcyclenum>
      <tasknum id="tasknum" style="width: 16.5%; height: 33%; float: left;"></tasknum>
      <auditreport id="auditreport" style="width: 33%; height: 33%; float: left;"></auditreport>
  </div>
</template>
<script >
import ECharts from 'vue-echarts/components/ECharts.vue'
import echarts from 'echarts'
import 'echarts/map/js/china'
import bingtu from '../bingtu/bingtu'
import zhutu from '../zhutu/zhutu'
import szhutu from '../zhutu/szhutu'
import auditreport from '../zhutu/auditreport'
import tasknum from '../zhutu/tasknum'
import onlineusers from '../zhutu/onlineusers'
import taskcyclenum from '../bingtu/taskcyclenum'
import quanguo from '../map/quanguo'
export default {
  name: 'ditu',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  },
  mounted () {
    setInterval(() => { this.option = this.option }, 100)
    // echarts.init(document.getElementById('mp')).setOption(this.option)
    // window.onresize = echarts.init(document.getElementById('mp')).resize
    window.onresize = function () {
      echarts.getInstanceByDom(document.getElementById('chartmap')).resize() // echart自适应,需要给元素指定大小
      echarts.getInstanceByDom(document.getElementById('liveacct')).resize()
      echarts.getInstanceByDom(document.getElementById('bingtu1')).resize()
      echarts.getInstanceByDom(document.getElementById('zhutu2')).resize()
      echarts.getInstanceByDom(document.getElementById('szhutu3')).resize()
      echarts.getInstanceByDom(document.getElementById('taskcyclenum')).resize()
      echarts.getInstanceByDom(document.getElementById('tasknum')).resize()
      echarts.getInstanceByDom(document.getElementById('auditreport')).resize()
    }
  },
  components: {
    'chart': ECharts,
    'bingtu': bingtu,
    'zhutu': zhutu,
    'szhutu': szhutu,
    'auditreport': auditreport,
    'taskcyclenum': taskcyclenum,
    'tasknum': tasknum,
    'onlineusers': onlineusers,
    'quanguo': quanguo
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
.mmap {
  position: relative;
  width: 100%;
  height: 100%;
  margin: 0px;
  padding: 0px;
  padding-top: 0%;
  background-size: 100% 100%;
}
</style>
