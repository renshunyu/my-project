<template>
  <chart id="auditreport" style="width: 100%; height: 100%; float: left;" :options="option"></chart>
</template>
<script >
import ECharts from 'vue-echarts/components/ECharts.vue'
import echarts from 'echarts'
export default {
  name: 'auditreport',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      option: {
        title: {
          text: '统计报表及其操作数',
          textStyle: {
            color: '#00ff00'
          },
          subtext: '纯属虚构'
        },
        tooltip: {
          trigger: 'axis'
        },
        legend: {
          data: ['降水量']
        },
        toolbox: {
          show: true,
          feature: {
            mark: {show: true},
            dataView: {show: true, readOnly: false},
            magicType: {show: true, type: ['line', 'bar']},
            restore: {show: true},
            saveAsImage: {show: true}
          }
        },
        calculable: true,
        xAxis: [
          {
            type: 'category',
            data: ['1月', '2月', '3月', '4月', '5月', '6月', '7月', '8月', '9月', '10月', '11月', '12月']
          }
        ],
        yAxis: [
          {
            type: 'value'
          }
        ],
        series: [
          {
            name: '降水量',
            type: 'bar',
            data: [2.6, 5.9, 9.0, 26.4, 28.7, 70.7, 175.6, 182.2, 48.7, 18.8, 6.0, 2.3],
            markPoint: {
              data: [
                {name: '年最高', value: 182.2, xAxis: 7, yAxis: 183, symbolSize: 18},
                {name: '年最低', value: 2.3, xAxis: 11, yAxis: 3}
              ]
            },
            markLine: {
              data: [
                {type: 'average', name: '平均值'}
              ]
            }
          }
        ]
      }
    }
  },
  mounted () {
    setInterval(() => { this.option = this.option }, 100)
    // echarts.init(document.getElementById('mp')).setOption(this.option)
    // window.onresize = echarts.init(document.getElementById('mp')).resize
    window.onresize = echarts.getInstanceByDom(document.getElementById('auditreport')).resize // echart自适应,需要给元素指定大小
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
