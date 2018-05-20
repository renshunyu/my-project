<template>
  <div id="mp" class="mmap">
      <chart id="chartmap" style="width: 39.6%; height: 65%; float: left;" :options="option"></chart>
      <chartuser id="liveacct" style="width: 26.4%; height: 65%; float: left;" :options="optionuser"></chartuser>
      <bingtu id="bingtu1" style="width: 33%; height: 33%; float: left;"></bingtu>
      <bingtu id="bingtu2" style="width: 33%; height: 33%; float: left;"></bingtu>
      <bingtu id="bingtu3" style="width: 33%; height: 33%; float: left;"></bingtu>
      <bingtu id="bingtu4" style="width: 33%; height: 33%; float: left;"></bingtu>
      <bingtu id="bingtu5" style="width: 33%; height: 33%; float: left;"></bingtu>
  </div>
</template>
<script >
import ECharts from 'vue-echarts/components/ECharts.vue'
import echarts from 'echarts'
import 'echarts/map/js/china'
import bingtu from '../bingtu/bingtu'
export default {
  name: 'ditu',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      option: {
        title: {
          text: '审计操作数 （2018-05）',
          subtext: '数据来自审计系统'
          // sublink: 'http://zh.wikipedia.org/wiki/%E9%A6%99%E6%B8%AF%E8%A1%8C%E6%94%BF%E5%8D%80%E5%8A%83#cite_note-12'
        },
        tooltip: {
          trigger: 'item',
          formatter: '{b}<br/>{c} (p / km2)'
        },
        toolbox: {
          show: true,
          orient: 'vertical',
          left: 'right',
          top: 'center',
          feature: {
            dataView: {readOnly: false},
            restore: {},
            saveAsImage: {}
          }
        },
        visualMap: {
          min: 800,
          max: 50000,
          text: ['High', 'Low'],
          realtime: false,
          calculable: true,
          inRange: {
            color: ['lightskyblue', 'yellow', 'orangered']
          }
        },
        series: [
          {
            name: '香港18区人口密度',
            type: 'map',
            mapType: 'china',
            itemStyle: {
              normal: { label: { show: true } },
              emphasis: { label: { show: true } }
            },
            data: [
              {name: '山西', value: 20057.34},
              {name: '北京', value: 15477.48},
              {name: '海南', value: 31686.1},
              {name: '南区', value: 6992.6},
              {name: '吉林', value: 44045.49},
              {name: '南海诸岛', value: 55204.26}
            ]
          }
        ]
      },
      optionuser: {
        title: {
          x: 'center',
          text: '移动业务支撑部门活跃用户数',
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
    window.onresize = function () {
      echarts.getInstanceByDom(document.getElementById('chartmap')).resize() // echart自适应,需要给元素指定大小
      echarts.getInstanceByDom(document.getElementById('liveacct')).resize()
      echarts.getInstanceByDom(document.getElementById('bingtu1')).resize()
      echarts.getInstanceByDom(document.getElementById('bingtu2')).resize()
      echarts.getInstanceByDom(document.getElementById('bingtu3')).resize()
      echarts.getInstanceByDom(document.getElementById('bingtu4')).resize()
      echarts.getInstanceByDom(document.getElementById('bingtu5')).resize()
    }
  },
  components: {
    'chart': ECharts,
    'chartuser': ECharts,
    'bingtu': bingtu
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
