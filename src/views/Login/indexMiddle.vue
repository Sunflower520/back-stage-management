<template>
  <div class="indexMiddle">
    <!-- 左侧 -->
    <div class="indexMiddle_left">
      <!-- 代办事项 -->
      <div class="Agent">
        <div class="title">
          <p>代办事项</p>
        </div>
        <div class="expect">
          <p>
            <span class="completed">
              <b>20</b>
            </span>
            <i style="color: green">已完成</i>
          </p>
          <p>
            <span class="incomplete"><b>20</b></span>
            <i style="color: red">未完成</i>
          </p>
          <p>
            <span class="overdue"><b>20</b></span>
            <i style="color: orange">逾期</i>
          </p>
        </div>
      </div>
      <!-- 图表 -->
      <div class="chart">
        <!-- 玫瑰图表 -->
        <div class="roseChart" style="width: 50%" height="100%">
          <div id="roseChartMain" style="width: 100%; height: 100%"></div>
        </div>
        <!-- 环形图表 -->
        <div class="annularChart" style="width: 50%" height="100%">
          <div id="annularChartMain" style="width: 100%; height: 100%"></div>
        </div>
      </div>
      <!-- 灌区概况 -->
      <div class="irrigatedSurvey">
        <el-table :data="tableData" border style="width: 100%" height="270">
          <el-table-column prop="date" label="灌区名称"> </el-table-column>
          <el-table-column prop="name" label="所属位置"> </el-table-column>
          <el-table-column prop="address" label="所属河流"> </el-table-column>
          <el-table-column prop="aaa" label="灌溉面积km²"> </el-table-column>
        </el-table>
      </div>
    </div>
    <!-- 中间 -->
    <div class="indexMiddle_between"></div>
    <!-- 右侧 -->
    <div class="indexMiddle_right">
      <!-- 降雨气象信息 -->
      <div class="meteorological"></div>
      <!-- 近24小时的雨量 -->
      <div class="rainfall">
        <div id="rainFallMain" style="width: 100%; height: 100%"></div>
      </div>
      <!-- 雷达图 -->
      <div class="radarMap"></div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      tableData: [
        {
          date: '双合灌区',
          name: '克什克腾旗',
          address: '百岔河',
          aaa: '100',
        },
        {
          date: '木系噶灌区',
          name: '克什克腾旗',
          address: '木石头匣子河（噶斯汰河）',
          aaa: '200',
        },
        {
          date: '东升灌区',
          name: '克什克腾旗',
          address: '木石头匣子河（噶斯汰河）',
          aaa: '123',
        },
        {
          date: '查干沐沦灌区',
          name: '林西县',
          address: '搏落沟儿河',
          aaa: '110',
        },
        {
          date: '钓鱼台灌区',
          name: '宁城县',
          address: '小城子河',
          aaa: '90',
        },
      ],
    }
  },
  mounted() {
    this.roseChartMain() // 玫瑰图表
    this.annularChartMain() // 环形图表
    this.rainFallMain() // 24小时降雨图表
  },
  methods: {
    // 玫瑰图表
    roseChartMain() {
      // 基于准备好的dom，初始化echarts实例
      let myChart = this.$echarts.init(document.getElementById('roseChartMain'))
      // 绘制图表
      myChart.setOption({
        legend: {
          // orient: 'vertical',
          bottom: 'bottom',
          itemGap: 5,
          textStyle: {
            //图例文字的样式
            color: '#fff',
            fontSize: 10,
          },
        },
        tooltip: {
          trigger: 'item',
        },
        series: [
          {
            name: '面积模式',
            type: 'pie',
            radius: '50%',
            center: ['50%', '30%'],
            roseType: 'area',
            label: {
              fontSize: 12,
              color: '#fff',
            },
            itemStyle: {
              normal: {
                label: {
                  show: false,
                  textStyle: {
                    //图例文字的样式
                    color: '#fff',
                    fontSize: 10,
                  },
                },
                labelLine: {
                  show: false,
                  // length: 1,
                },
              },
            },
            data: [
              { value: 40, name: 'rose1' },
              { value: 38, name: 'rose2' },
              { value: 32, name: 'rose3' },
              { value: 30, name: 'rose4' },
              { value: 28, name: 'rose5' },
            ],
          },
        ],
      })
    },
    // 环形图表
    annularChartMain() {
      // 基于准备好的dom，初始化echarts实例
      let myChart = this.$echarts.init(
        document.getElementById('annularChartMain')
      )
      // 绘制图表
      myChart.setOption({
        tooltip: {
          trigger: 'item',
        },
        // legend: {
        //   // orient: 'vertical',
        //   right: 'right',
        //   top: '5%',
        //   itemGap: 5,
        //     textStyle: {
        //     //图例文字的样式
        //     color: '#fff',
        //     fontSize: 10,
        //   },
        // },
        legend: {
          // orient: 'vertical',
          bottom: 'bottom',
          itemGap: 5,
          textStyle: {
            //图例文字的样式
            color: '#fff',
            fontSize: 10,
          },
        },
        series: [
          {
            name: '面积模式',
            type: 'pie',
            radius: ['30%', '50%'],
            center: ['50%', '30%'],
            avoidLabelOverlap: false,
            label: {
              show: false,
              position: 'center',
            },
            emphasis: {
              label: {
                show: true,
                fontSize: '10',
                fontWeight: 'bold',
                color: '#fff',
              },
            },
            labelLine: {
              show: false,
            },
            data: [
              { value: 1048, name: 'annular1' },
              { value: 735, name: 'annular2' },
              { value: 580, name: 'annular3' },
              { value: 484, name: 'annular4' },
              { value: 300, name: 'annular5' },
            ],
          },
        ],
      })
    },
    // 24小时降雨图表
    rainFallMain() {
      let myChart = this.$echarts.init(document.getElementById('rainFallMain'))
      myChart.setOption({
        title: {
          text: '近24小时雨量',
          left: 'center',
          textStyle: {
            color: '#fff',
            fontSize: 14,
          },
        },
        tooltip: {
          trigger: 'axis',
          axisPointer: {
            type: 'shadow',
          },
        },
        grid: {
          x: 38,
          y: 25,
          x2: 30,
          y2: 20,
        },
        xAxis: [
          {
            type: 'category',
            data: ['双合', '木系噶', '东升', '查干沐沦', '钓鱼台'],
            axisLabel: {
              //坐标轴刻度标签的相关设置。
              interval: 0,
              rotate: '0',
            },
            axisTick: {
              alignWithLabel: true,
            },
            splitLine: {
              show: true,
              lineStyle: {
                color: 'skyblue',
              },
            },
          },
        ],
        yAxis: [
          {
            type: 'value',
            name: '本月降雨',
            nameTextStyle: {
              color: '#fff',
              fontSize: 10,
            },
            min: 0,
            max: 1000,
            interval: 200,
            axisLabel: {
              textStyle: {
                color: '#fff',
              },
            },
          },
          {
            type: 'value',
            name: '当前降雨',
            nameTextStyle: {
              color: '#fff',
              fontSize: 10,
            },
            min: 0,
            max: 25,
            interval: 5,
            axisLabel: {
              formatter: '{value}',
              textStyle: {
                color: '#fff',
              },
            },
            splitLine: {
              show: true,
              lineStyle: {
                color: 'skyblue',
              },
            },
          },
        ],
        series: [
          {
            name: '本月降雨',
            type: 'bar',
            barWidth: '60%',
            data: [100, 52, 200, 334, 390, 330, 220],
          },
          {
            name: '当前降雨',
            data: [10, 0, 26, 35, 0, 33, 15],
            type: 'line',
          },
        ],
      })
    },
  },
}
</script>
<style lang="scss" scoped>
.indexMiddle {
  box-sizing: border-box;
  width: 100%;
  height: 64%;
  //   background-color: pink;
  //   左侧
  .indexMiddle_left {
    box-sizing: border-box;
    float: left;
    width: 20%;
    height: 100%;
    // 左侧-代办事项
    .Agent {
      box-sizing: border-box;
      width: 100%;
      height: 20%;
      padding: 10px 15px;
      margin-bottom: 2%;
      border: 2px solid skyblue;
      border-radius: 16px;
      .title {
        width: 30%;
        height: 100%;
        float: left;
        p {
          color: #fff;
          font-size: 20px;
          font-weight: 600;
        }
      }
      .expect {
        display: flex;
        width: 70%;
        height: 100%;
        float: right;
        p {
          flex: 1;
          padding: 10px;
          .completed {
            box-sizing: border-box;
            display: block;
            height: 60%;
            border: 6px solid green;
            border-radius: 50% 50%;
            b {
              color: #fff;
              margin-left: 20%;
              font-size: 22px;
              line-height: 36px;
            }
          }
          .incomplete {
            box-sizing: border-box;
            display: block;
            height: 60%;
            border: 6px solid red;
            border-radius: 50% 50%;
            b {
              color: #fff;
              margin-left: 20%;
              font-size: 22px;
              line-height: 36px;
            }
          }
          .overdue {
            box-sizing: border-box;
            display: block;
            height: 60%;
            border: 6px solid orange;
            border-radius: 50% 50%;
            b {
              color: #fff;
              margin-left: 20%;
              font-size: 22px;
              line-height: 36px;
            }
          }
          i {
            box-sizing: border-box;
            display: block;
            height: 40%;
            text-align: center;
            line-height: 44px;
            font-weight: 600;
          }
        }
      }
    }
    // 左侧-玫瑰图表
    .chart {
      display: flex;
      box-sizing: border-box;
      width: 100%;
      height: 30%;
      padding: 10px 15px;
      margin-bottom: 2%;
      border: 2px solid skyblue;
      border-radius: 16px;
    }
    // 左侧-灌区概况
    .irrigatedSurvey {
      box-sizing: border-box;
      width: 100%;
      height: 47%;
      padding: 10px 15px;
      //   margin-bottom: 2%;x
      border: 2px solid skyblue;
      border-radius: 16px;
      //   /deep/.el-table--scrollable-x ::-webkit-scrollbar {
      //     display: none;
      //   }
      //   /deep/ .el-table td, .el-table th {
      //       padding: 0;
      //   }
      //   表头字体颜色
      /deep/ .el-table thead {
        color: skyblue;
      }
      //   表身字体颜色
      /deep/ .el-table {
        color: #fff;
      }
      //   表头背景颜色
      /deep/ .el-table th,
      .el-table tr {
        background-color: rgb(5, 14, 59) !important;
      }
      //   表身背景颜色
      /deep/.el-table__row {
        background-color: rgb(5, 14, 59) !important;
      }
      //   选中颜色透明
      /deep/ .el-table--enable-row-hover .el-table__body tr:hover > td {
        background-color: transparent;
      }
      //   边框线颜色开始
      //   /deep/ .el-table th.is-leaf {
      //     border-bottom: 1px solid skyblue !important;
      //   }
      //   /deep/ .el-table td,
      //   .el-table th.is-leaf {
      //     border-bottom: 1px solid skyblue !important;
      //   }
      //   /deep/ .el-table--border td,
      //   .el-table--border th,
      //   .el-table__body-wrapper
      //     .el-table--border.is-scrolling-left
      //     ~ .el-table__fixed {
      //     border-right: 1px solid skyblue !important;
      //   }
      //   /deep/ .el-table--border, .el-table--group {
      //       border: 1px solid skyblue !important;
      //   }
      // 边框线颜色结束
    }
  }
  //   中间
  .indexMiddle_between {
    box-sizing: border-box;
    float: left;
    width: 60%;
    height: 100%;
  }
  //   右侧
  .indexMiddle_right {
    box-sizing: border-box;
    float: right;
    width: 20%;
    height: 100%;
    .meteorological {
      box-sizing: border-box;
      width: 100%;
      height: 20%;
      padding: 10px 15px;
      margin-bottom: 2%;
      border: 2px solid skyblue;
      border-radius: 16px;
    }
    .rainfall {
      box-sizing: border-box;
      width: 100%;
      height: 30%;
      padding: 10px 15px;
      margin-bottom: 2%;
      border: 2px solid skyblue;
      border-radius: 16px;
    }
    .radarMap {
      box-sizing: border-box;
      width: 100%;
      height: 47%;
      padding: 10px 15px;
      //   margin-bottom: 2%;x
      border: 2px solid skyblue;
      border-radius: 16px;
    }
  }
}
</style>
