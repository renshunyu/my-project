<template>
  <chart id="quanguo" style="width: 100%; height: 100%; float: left;" :options="option"></chart>
</template>
<script >
import ECharts from 'vue-echarts/components/ECharts.vue'
import echarts from 'echarts'
import 'echarts/map/js/china'
export default {
  name: 'quanguo',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      option: {
        title: {
          text: '审计操作数 （2018-05）',
          textStyle: {
            color: '#00ff00'
          },
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
      }
    }
  },
  mounted () {
    setInterval(() => { this.option = this.option }, 100)
    // echarts.init(document.getElementById('mp')).setOption(this.option)
    // window.onresize = echarts.init(document.getElementById('mp')).resize
    window.onresize = echarts.getInstanceByDom(document.getElementById('quanguo')).resize // echart自适应,需要给元素指定大小
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
