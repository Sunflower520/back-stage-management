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
          <div id="expectMain" style="width: 100%; height: 100%"></div>
          <!-- <p>
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
          </p> -->
        </div>
      </div>
      <!-- 图表 -->
      <div class="chart">
        <!-- 玫瑰图表 -->
        <div class="roseChart" style="width: 100%" height="100%">
          <div id="roseChartMain" style="width: 100%; height: 100%"></div>
        </div>
        <!-- 环形图表 -->
        <!-- <div class="annularChart" style="width: 50%" height="100%">
          <div id="annularChartMain" style="width: 100%; height: 100%"></div>
        </div> -->
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
    // this.annularChartMain() // 环形图表
    this.rainFallMain() // 24小时降雨图表
    this.expectMain() //
  },
  methods: {
    expectMain() {
      let myChart = this.$echarts.init(document.getElementById('expectMain'))
      myChart.setOption({
        series: [
          {
            name: '已完成',
            type: 'pie',
            radius: ['42%', '48%'],
            center: ['15%', '50%'],
            startAngle: 225,
            color: [
              new this.$echarts.graphic.LinearGradient(0, 0, 0, 1, [
                {
                  offset: 0,
                  color: '#f1d72b',
                },
                {
                  offset: 1,
                  color: '#cf7f14',
                },
              ]),
              'transparent',
            ],
            labelLine: {
              normal: {
                show: false,
              },
            },
            label: {
              normal: {
                position: 'center',
              },
            },
            data: [
              {
                value: 75,
                name: '已完成',
                label: {
                  normal: {
                    formatter: '已完成',
                    textStyle: {
                      color: '#fff',
                      fontSize: 14,
                    },
                  },
                },
              },
              {
                value: 25,
                name: '%',
                label: {
                  normal: {
                    formatter: '\n\n35',
                    textStyle: {
                      color: '#FFDB5C',
                      fontSize: 24,
                    },
                  },
                },
              },
              {
                value: 0,
                name: '%',
                label: {
                  normal: {
                    formatter: '',
                    textStyle: {
                      color: '#fff',
                      fontSize: 14,
                    },
                  },
                },
              },
            ],
          },
          {
            name: '未完成',
            type: 'pie',
            radius: ['42%', '48%'],
            center: ['50%', '50%'],
            startAngle: 225,
            color: [
              new this.$echarts.graphic.LinearGradient(0, 0, 0, 1, [
                {
                  offset: 0,
                  color: '#16e5cc',
                },
                {
                  offset: 1,
                  color: '#139dd6',
                },
              ]),
              'transparent',
            ],
            labelLine: {
              normal: {
                show: false,
              },
            },
            label: {
              normal: {
                position: 'center',
              },
            },
            data: [
              {
                value: 75,
                name: '未完成',
                label: {
                  normal: {
                    formatter: '未完成',
                    textStyle: {
                      color: '#fff',
                      fontSize: 14,
                    },
                  },
                },
              },
              {
                value: 25,
                name: '%',
                label: {
                  normal: {
                    formatter: '\n\n22',
                    textStyle: {
                      color: '#007ac6',
                      fontSize: 24,
                    },
                  },
                },
              },
              {
                value: 0,
                name: '%',
                label: {
                  normal: {
                    formatter: '',
                    textStyle: {
                      color: '#fff',
                      fontSize: 14,
                    },
                  },
                },
              },
            ],
          },
          {
            name: '超期',
            type: 'pie',
            radius: ['42%', '48%'],
            center: ['85%', '50%'],
            startAngle: 225,
            labelLine: {
              normal: {
                show: false,
              },
            },
            label: {
              normal: {
                position: 'center',
              },
            },
            data: [
              {
                value: 75,
                itemStyle: {
                  normal: {
                    color: new this.$echarts.graphic.LinearGradient(
                      0,
                      0,
                      0,
                      1,
                      [
                        {
                          offset: 0,
                          color: '#5d0f1c',
                        },
                        {
                          offset: 1,
                          color: '#ef0027',
                        },
                      ]
                    ),
                  },
                },
                name: '超期',
                label: {
                  normal: {
                    formatter: '超期',
                    textStyle: {
                      color: '#fff',
                      fontSize: 14,
                    },
                  },
                },
              },
              {
                value: 25,
                name: '%',
                label: {
                  normal: {
                    formatter: '\n\n9',
                    textStyle: {
                      color: '#ef0027',
                      fontSize: 24,
                    },
                  },
                },
              },
              {
                value: 0,
                name: '%',
                label: {
                  normal: {
                    formatter: '',
                    textStyle: {
                      color: '#fff',
                      fontSize: 16,
                    },
                  },
                },
              },
            ],
          },
        ],
      })
    },
    // 玫瑰图表
    roseChartMain() {
      // 基于准备好的dom，初始化echarts实例
      let myChart = this.$echarts.init(document.getElementById('roseChartMain'))
      // 绘制图表
      myChart.setOption({
        // backgroundColor: '#000',
        tooltip: {
          trigger: 'item',
          formatter: '{a} <br/>{b} : {c}千万元',
        },
        legend: {
          x: 'center',
          y: '15%',
          data: ['义乌市1', '义乌市2', '义乌市3'],
          icon: 'circle',
          textStyle: {
            color: '#fff',
          },
        },
        calculable: true,
        series: [
          {
            name: '可疑群众线索',
            type: 'pie',
            //起始角度，支持范围[0, 360]
            startAngle: 0,
            //饼图的半径，数组的第一项是内半径，第二项是外半径
            radius: ['100%', '10%'],
            //支持设置成百分比，设置成百分比时第一项是相对于容器宽度，第二项是相对于容器高度
            center: ['50%', '35%'],
            //是否展示成南丁格尔图，通过半径区分数据大小。可选择两种模式：
            // 'radius' 面积展现数据的百分比，半径展现数据的大小。
            //  'area' 所有扇区面积相同，仅通过半径展现数据大小
            roseType: 'area',
            //是否启用防止标签重叠策略，默认开启，圆环图这个例子中需要强制所有标签放在中心位置，可以将该值设为 false。
            avoidLabelOverlap: false,
            label: {
              normal: {
                show: true,
                formatter: '{d}%',
              },
              emphasis: {
                show: true,
              },
            },
            itemStyle: {
              shadowColor: '#19181d',
              shadowBlur: 30,
            },
            labelLine: {
              normal: {
                show: true,
              },
              emphasis: {
                show: true,
              },
            },
            data: [
              {
                value: 600,
                name: '已完成',
                label: {
                  color: '#FDD56A',
                },
                itemStyle: {
                  normal: {
                    color: '#FDD56A',
                    color: {
                      type: 'linear',
                      x: 0,
                      y: 0,
                      x2: 0,
                      y2: 1,
                      colorStops: [
                        {
                          offset: 1,
                          color: '#f1d72b', // 0% 处的颜色
                        },
                        {
                          offset: 1,
                          color: '#cf7f14', // 100% 处的颜色
                        },
                      ],
                      global: false, // 缺省为 false
                    },
                  },
                },
              },
              {
                value: 1100,
                name: '未完成',
                label: {
                  color: '#16e5cc',
                },
                itemStyle: {
                  normal: {
                    color: {
                      type: 'linear',
                      x: 0,
                      y: 0,
                      x2: 0,
                      y2: 1,
                      colorStops: [
                        {
                          offset: 0,
                          color: '#16e5cc', // 0% 处的颜色
                        },
                        {
                          offset: 1,
                          color: '#139dd6', // 100% 处的颜色
                        },
                      ],
                      global: false, // 缺省为 false
                    },
                  },
                },
              },
              {
                value: 1200,
                name: '超期',
                label: {
                  color: '#ef0027',
                },
                itemStyle: {
                  normal: {
                    color: {
                      type: 'linear',
                      x: 0,
                      y: 0,
                      x2: 0,
                      y2: 1,
                      colorStops: [
                        {
                          offset: 0,
                          color: '#5d0f1c', // 0% 处的颜色
                        },
                        {
                          offset: 1,
                          color: '#ef0027', // 100% 处的颜色
                        },
                      ],
                      global: false, // 缺省为 false
                    },
                  },
                },
              },
              {
                value: 0,
                name: '',
                itemStyle: {
                  normal: {
                    color: 'transparent',
                  },
                },
                label: {
                  show: false,
                },
                labelLine: {
                  show: false,
                },
              },
              {
                value: 0,
                name: '',
                itemStyle: {
                  normal: {
                    color: 'transparent',
                  },
                },
                label: {
                  show: false,
                },
                labelLine: {
                  show: false,
                },
              },
              {
                value: 0,
                name: '',
                itemStyle: {
                  normal: {
                    color: 'transparent',
                  },
                },
                label: {
                  show: false,
                },
                labelLine: {
                  show: false,
                },
              },
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
              textStyle: {
                color: '#fff',
              },
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
            barWidth: '80%',
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
        width: 100%;
        // height: 100%;
        // float: left;
        p {
          color: #fff;
          font-size: 20px;
          font-weight: 600;
        }
      }
      .expect {
        display: flex;
        width: 100%;
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
