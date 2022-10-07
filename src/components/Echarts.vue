
<template>
  <div class="about" style="display:flex;width:100%;flex-wrap:wrap">
        <div id="myChart" :style="{width: '300px', height: '300px'}"></div>
        <div id="myChart1" :style="{width: '300px', height: '300px'}"></div>
        <div id="myChart2" :style="{width: '300px', height: '300px'}"></div>
        <div id="myChart3" :style="{width: '300px', height: '300px'}"></div>
        <div id="myChart4" :style="{width: '300px', height: '300px'}"></div>
        <div id="myChart5" :style="{width: '300px', height: '300px'}"></div>
        <div id="myChart6" :style="{width: '300px', height: '300px',marginBottom:'200px'}"></div>
      </div>
</template>
<script>
// import echarts from 'echarts'
let Echarts = require('echarts/lib/echarts');

export default {
  name: 'EchartsDemo',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  },
  mounted(){
      console.log(Echarts)
      this.drawLine('myChart');
      this.drawLine('myChart1');
      this.drawLine('myChart2');
      this.drawLine('myChart3');
      this.drawLine('myChart4');
      this.drawLine('myChart5');
      this.drawLine('myChart6');

  },
  methods: {
    drawLine(val){
        // 基于准备好的dom，初始化echarts实例
        console.log(Echarts)
        let myChart = Echarts.init(document.getElementById(val))
        console.log('123',myChart)
        // 绘制图表
        myChart.setOption({
            title: { text: 'echarts' },
            tooltip: {},
            xAxis: {
                data: ["衬衫","羊毛衫","雪纺衫","裤子","高跟鞋","袜子"],
                axisLabel: {
                show: true,
                  textStyle: {
                    color: '#c3dbff',  //更改坐标轴文字颜色
                    fontSize : 14,      //更改坐标轴文字大小
                    backgroundColor:'red'
                  }
              },
            },
            textStyle: {
                    color: function (value, index) {
                        return value >= 0 ? 'green' : 'red';
                      },
                    },
            yAxis: {
              axisLabel: {
                show: true,
                  textStyle: {
                    color: '#c3dbff',  //更改坐标轴文字颜色
                    fontSize : 14,      //更改坐标轴文字大小
                    backgroundColor:'blue',
                    width:'200px',
                    height:'300px'
                  
                  }
              },
            },
            series: [{
                name: '销量',
                type: 'bar',
                data: [5, 20, 36, 10, 10, 20]
            }]
        });
    }
  }
}
</script>