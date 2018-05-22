<template>
  <chart id="taskcyclenum" style="width: 100%; height: 100%; float: left;" :options="option"></chart>
</template>
<script >
import ECharts from 'vue-echarts/components/ECharts.vue'
import echarts from 'echarts'
export default {
  name: 'taskcyclenum',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      option: {
        title: {
          text: '审计任务场景纳入数',
          subtext: '纯属虚构',
          x: 'center'
        },
        tooltip: {
          trigger: 'item',
          formatter: '{a} <br/>{b}: {c} ({d}%)'
        },
        legend: {
          orient: 'vertical',
          x: 'left',
          data: ['直接访问', '邮件营销', '联盟广告']
        },
        calculable: true,
        series: [
          {
            name: '访问来源',
            type: 'pie',
            radius: '55%',
            center: ['50%', '60%'],
            data: [
              {value: 335, name: '直接访问'},
              {value: 310, name: '邮件营销'},
              {value: 234, name: '联盟广告'}
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
    window.onresize = echarts.getInstanceByDom(document.getElementById('taskcyclenum')).resize // echart自适应,需要给元素指定大小
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
