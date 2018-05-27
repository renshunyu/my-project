<template>
  <chart id="onlineusers" style="width: 100%; height: 100%; float: left;" :options="option"></chart>
</template>
<script >
import ECharts from 'vue-echarts/components/ECharts.vue'
import echarts from 'echarts'
export default {
  name: 'onlineusers',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      option: {
        title: {
          x: 'center',
          text: '移动业务支撑部门活跃用户数',
          textStyle: {
            color: '#00ff00'
          },
          subtext: 'Rainbow bar example',
          link: 'http://echarts.baidu.com/doc/example.html'
        },
        color: ['#3398DB'],
        tooltip: {
          trigger: 'axis',
          axisPointer: {// 坐标轴指示器，坐标轴触发有效
            type: 'shadow'// 默认为直线，可选为：'line' | 'shadow'
          }
        },
        grid: {
          left: '3%',
          right: '4%',
          bottom: '3%',
          containLabel: true
        },
        xAxis: [
          {
            type: 'value'
          }
        ],
        yAxis: [
          {
            type: 'category',
            data: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun'],
            axisTick: {
              alignWithLabel: true
            }
          }
        ],
        series: [
          {
            name: '直接访问',
            type: 'bar',
            barWidth: '60%',
            data: [10, 52, 200, 334, 390, 330, 220]
          }
        ]
      }
    }
  },
  mounted () {
    setInterval(() => { this.option = this.option }, 100)
    // echarts.init(document.getElementById('mp')).setOption(this.option)
    // window.onresize = echarts.init(document.getElementById('mp')).resize
    window.onresize = echarts.getInstanceByDom(document.getElementById('onlineusers')).resize // echart自适应,需要给元素指定大小
  },
  components: {
    'chart': ECharts
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
.mroot {
  position: relative;
  width: 100%;
  height: 100%;
  margin: 0px;
  padding: 0px;
  padding-top: 0%;
  background-size: 100% 100%;
}
</style>
