<template>
  <div style="height:500px">
    <el-table :data="tableData3" height="100%" border style="width: 100%">
      <el-table-column prop="date" label="日期" width="180">
      </el-table-column>
      <el-table-column prop="name" label="姓名" width="180">
      </el-table-column>
      <el-table-column prop="address" label="地址">
      </el-table-column>
    </el-table>
    <div id='main' style="width: 600px;height:400px;">

    </div>
  </div>

</template>

<script>
import lay from './lay.vue'
export default {
  async created() {


  },
  components: {
    lay
  },
  mounted() {
    this.myCharts2()
  },
  methods: {
    myCharts2() {
      let myChart = this.echarts.init(document.getElementById('main'));
      let option = {
        color: ['#3398DB'],
        tooltip: {
          trigger: 'axis',
          axisPointer: {            // 坐标轴指示器，坐标轴触发有效
            type: 'shadow'        // 默认为直线，可选为：'line' | 'shadow'
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
            type: 'category',
            data: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun'],
            axisTick: {
              alignWithLabel: true
            }
          }
        ],

        yAxis: [
          {
            type: 'value'
          }
        ],
        series: [
          {
            name: '直接访问',
            type: 'bar',
            barWidth: '60%',
            data: [10, 52, 200, 334, 390, 330, 220],
            itemStyle: {
              normal: {
                label: {
                  show: true,
                  position: 'top',
                  textStyle: {
                    color: '#615a5a'
                  },
                  formatter: function (params) {
                    console.log(params)
                    if (params.value == 0) {
                      return '';
                    } else {
                      return params.value+'\n\n'+3;
                    }
                  }
                }
              }
            },
          }
        ]
      };
      myChart.setOption(option);

    },
    myCharts() {
      let myChart = this.echarts.init(document.getElementById('main'));

      let option = {
        title: {
          text: '折线图堆叠'
        },
        // tooltip: {
        //   trigger: 'axis',
        //   axisPointer: {            // 坐标轴指示器，坐标轴触发有效
        //     type: 'shadow',        // 默认为直线，可选为：'line' | 'shadow'
        //   }
        // },
        tooltip: {
          trigger: 'axis',
          axisPointer: {            // 坐标轴指示器，坐标轴触发有效
            type: 'shadow',        // 默认为直线，可选为：'line' | 'shadow'
          },
          formatter: function (params) {
            // params.map
            // console.log(params)
            let str = params[0].axisValue + '<br/>'
            params.forEach(item => {
              str += item.marker + item.seriesName + ':' + item.value + '%' + '<br/>'
            })
            return str
            // return params[0].name + params[0].value '<br />' + params[1].value;
          }
        },
        legend: {
          data: ['邮件营销', '联盟广告', '视频广告', '直接访问', '搜索引擎']
        },
        grid: {
          left: '3%',
          right: '4%',
          bottom: '3%',
          containLabel: true
        },
        xAxis: {
          type: 'category',
          boundaryGap: false,
          data: ['周一', '周二', '周三']
        },
        toolbox: {
          show: true,
          feature: {
            dataView: { show: true, readOnly: false },
            magicType: { show: true, type: ['line', 'bar'] },
            restore: { show: true },
            saveAsImage: { show: true }
          }
        },
        itemStyle: {
          normal: {
            label: {
              show: true,
              position: 'top',
              textStyle: {
                color: '#615a5a'
              },
              formatter: function (params) {
                if (params.value == 0) {
                  return '';
                } else {
                  return params.value;
                }
              }
            }
          }
        },

        yAxis: [{
          type: 'value',
          axisLabel: {
            show: true,
            // textStyle: {
            //   color: '#3398DB',
            //   fontSize: '50%',
            // },
            // interval: 0,
            // showMinLabel: true,
            formatter: '{value} %'
          },
          // min: 90,
          max: 100,
          splitNumber: 10
        }],


        series: [
          {
            name: '邮件营销',
            type: 'line',
            data: [48, 60, 70]
          },
          {
            name: '联盟广告',
            type: 'line',
            data: [48, 60, 70]
          },
          {
            name: '联盟广告',
            type: 'line',
            data: [48, 60, 70]
          },
        ]

      };

      myChart.setOption(option);
    }
  },
  data() {
    return {
      a: false,
      tableData3: [{
        date: '2016-05-03',
        name: '王小虎',
        address: '上海市普陀区金沙江路 1518 弄'
      }, {
        date: '2016-05-02',
        name: '王小虎',
        address: '上海市普陀区金沙江路 1518 弄'
      }, {
        date: '2016-05-04',
        name: '王小虎',
        address: '上海市普陀区金沙江路 1518 弄'
      }, {
        date: '2016-05-01',
        name: '王小虎',
        address: '上海市普陀区金沙江路 1518 弄'
      }, {
        date: '2016-05-08',
        name: '王小虎',
        address: '上海市普陀区金沙江路 1518 弄'
      }, {
        date: '2016-05-06',
        name: '王小虎',
        address: '上海市普陀区金沙江路 1518 弄'
      }, {
        date: '2016-05-07',
        name: '王小虎',
        address: '上海市普陀区金沙江路 1518 弄'
      }, {
        date: '2016-05-07',
        name: '王小虎',
        address: '上海市普陀区金沙江路 1518 弄'
      }, {
        date: '2016-05-07',
        name: '王小虎',
        address: '上海市普陀区金沙江路 1518 弄'
      }, {
        date: '2016-05-07',
        name: '王小虎',
        address: '上海市普陀区金沙江路 1518 弄'
      }, {
        date: '2016-05-07',
        name: '王小虎',
        address: '上海市普陀区金沙江路 1518 弄'
      }, {
        date: '2016-05-07',
        name: '王小虎',
        address: '上海市普陀区金沙江路 1518 弄'
      }, {
        date: '2016-05-07',
        name: '王小虎',
        address: '上海市普陀区金沙江路 1518 弄'
      }, {
        date: '2016-05-07',
        name: '王小虎',
        address: '上海市普陀区金沙江路 1518 弄'
      }, {
        date: '2016-05-07',
        name: '王小虎',
        address: '上海市普陀区金沙江路 1518 弄'
      }, {
        date: '2016-05-07',
        name: '王小虎',
        address: '上海市普陀区金沙江路 1518 弄'
      }]
    }
  }
}
</script>