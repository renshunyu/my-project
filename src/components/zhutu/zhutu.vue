<template>
  <chart id="zhutu" style="width: 100%; height: 100%; float: left;" :options="option"></chart>
</template>
<script >
import ECharts from 'vue-echarts/components/ECharts.vue'
import echarts from 'echarts'
export default {
  name: 'zhutu',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      option: {
        title: {
          x: 'center',
          text: '智能审计查询日志数',
          textStyle: {
            color: '#00ff00'
          },
          subtext: 'Rainbow bar example',
          link: 'http://echarts.baidu.com/doc/example.html'
        },
        tooltip: {
          trigger: 'item'
        },
        toolbox: {
          show: true,
          feature: {
            dataView: {show: true, readOnly: false},
            restore: {show: true},
            saveAsImage: {show: true}
          }
        },
        calculable: true,
        grid: {
          borderWidth: 0,
          y: 80,
          y2: 60
        },
        xAxis: [
          {
            type: 'category',
            show: false,
            data: ['Line', 'Bar', 'Scatter', 'K', 'Pie', 'Radar', 'Chord', 'Force', 'Map', 'Gauge', 'Funnel']
          }
        ],
        yAxis: [
          {
            type: 'value',
            show: false
          }
        ],
        series: [
          {
            name: 'ECharts例子个数统计',
            type: 'bar',
            itemStyle: {
              normal: {
                color: function (params) {
                  // build a color map as your need.
                  var colorList = [
                    '#C1232B', '#B5C334', '#FCCE10', '#E87C25', '#27727B',
                    '#FE8463', '#9BCA63', '#FAD860', '#F3A43B', '#60C0DD',
                    '#D7504B', '#C6E579', '#F4E001', '#F0805A', '#26C0C0'
                  ]
                  return colorList[params.dataIndex]
                },
                label: {
                  show: true,
                  position: 'top',
                  formatter: '{b}\n{c}'
                }
              }
            },
            data: [12, 21, 10, 4, 12, 5, 6, 5, 25, 23, 7],
            markPoint: {
              tooltip: {
                trigger: 'item',
                backgroundColor: 'rgba(0, 0, 0, 0)',
                formatter: function (params) {
                  return '<img src="' +
                  params.data.symbol.replace('image://', '') +
                  '"/>'
                }
              },
              data: [
                {xAxis: 0, y: 350, name: 'Line', symbolSize: 20, symbol: 'image://../asset/ico/折线图.png'},
                {xAxis: 1, y: 350, name: 'Bar', symbolSize: 20, symbol: 'image://../asset/ico/柱状图.png'},
                {xAxis: 2, y: 350, name: 'Scatter', symbolSize: 20, symbol: 'image://../asset/ico/散点图.png'},
                {xAxis: 3, y: 350, name: 'K', symbolSize: 20, symbol: 'image://../asset/ico/K线图.png'},
                {xAxis: 4, y: 350, name: 'Pie', symbolSize: 20, symbol: 'image://../asset/ico/饼状图.png'},
                {xAxis: 5, y: 350, name: 'Radar', symbolSize: 20, symbol: 'image://../asset/ico/雷达图.png'},
                {xAxis: 6, y: 350, name: 'Chord', symbolSize: 20, symbol: 'image://../asset/ico/和弦图.png'},
                {xAxis: 7, y: 350, name: 'Force', symbolSize: 20, symbol: 'image://../asset/ico/力导向图.png'},
                {xAxis: 8, y: 350, name: 'Map', symbolSize: 20, symbol: 'image://../asset/ico/地图.png'},
                {xAxis: 9, y: 350, name: 'Gauge', symbolSize: 20, symbol: 'image://../asset/ico/仪表盘.png'},
                {xAxis: 10, y: 350, name: 'Funnel', symbolSize: 20, symbol: 'image://../asset/ico/漏斗图.png'}
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
    window.onresize = echarts.getInstanceByDom(document.getElementById('zhutu')).resize // echart自适应,需要给元素指定大小
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
