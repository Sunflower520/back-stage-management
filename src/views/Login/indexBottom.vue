<template>
  <div class="indexButton">
    <div class="indexButton_left">
      <el-table :data="tableData" border style="width: 100%" height="230">
        <el-table-column prop="date" label="灌区名称" width="100">
        </el-table-column>
        <el-table-column prop="name" label="水位" width="50"> </el-table-column>
        <el-table-column prop="address" label="开度" width="50">
        </el-table-column>
        <el-table-column prop="aaa" label="检测时间"> </el-table-column>
      </el-table>
    </div>
    <div class="indexButton_between">
      <div id="waterStatisticsMain" style="width: 100%; height: 100%"></div>
    </div>
    <div class="indexButton_right"></div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      tableData: [
        {
          date: '双合灌区',
          name: '11',
          address: '15',
          aaa: '06-09 18:21:03',
        },
        {
          date: '木系噶灌区',
          name: '9',
          address: '5',
          aaa: '06-09 18:31:03',
        },
        {
          date: '东升灌区',
          name: '7',
          address: '11',
          aaa: '06-09 18:20:03',
        },
        {
          date: '查干沐沦灌区',
          name: '8',
          address: '7',
          aaa: '06-09 18:23:03',
        },
        {
          date: '钓鱼台灌区',
          name: '10',
          address: '12',
          aaa: '06-09 18:24:03',
        },
      ],
    }
  },
  mounted() {
    this.waterStatisticsMain() //灌区水量统计
  },
  methods: {
    //灌区水量统计
    waterStatisticsMain() {
      let myChart = this.$echarts.init(
        document.getElementById('waterStatisticsMain')
      )
      myChart.setOption({
        title: {
          text: '灌区水量统计',
          textStyle: {
            //图例文字的样式
            color: '#fff',
          },
        },
        grid: {
          x: 50,
          y: 45,
          x2: 50,
          y2: 20,
        },
        tooltip: {
          trigger: 'axis',
          axisPointer: {
            type: 'cross',
            crossStyle: {
              color: '#999',
            },
          },
        },

        legend: {
          right: '5%',
          orient: 'horizontal',
          data: ['蒸发量', '降水量', '平均温度'],
          textStyle: {
            //图例文字的样式
            color: '#fff',
            fontSize: 12,
          },
        },
        xAxis: [
          {
            type: 'category',
            data: [
              '1月',
              '2月',
              '3月',
              '4月',
              '5月',
              '6月',
              '7月',
              '8月',
              '9月',
              '10月',
              '11月',
              '12月',
            ],
            axisPointer: {
              type: 'shadow',
            },
            axisLabel: {
              textStyle: {
                color: '#fff',
              },
            },
            splitLine: {
              show: true,
              lineStyle: {
                color: 'skyblue',
                //   type: 'dashed',
              },
            },
          },
        ],
        yAxis: [
          {
            type: 'value',
            min: 0,
            max: 250,
            interval: 50,
            axisLabel: {
              formatter: '{value} ml',
              textStyle: {
                color: '#fff',
              },
            },
          },
          {
            type: 'value',
            min: 0,
            max: 25,
            interval: 5,
            axisLabel: {
              formatter: '{value} °C',
              textStyle: {
                color: '#fff',
              },
            },
            splitLine: {
              show: true,
              lineStyle: {
                color: 'skyblue',
                //   type: 'dashed',
              },
            },
          },
        ],
        series: [
          {
            name: '蒸发量',
            type: 'bar',
            data: [
              2.0,
              4.9,
              7.0,
              23.2,
              25.6,
              76.7,
              135.6,
              162.2,
              32.6,
              20.0,
              6.4,
              3.3,
            ],
          },
          {
            name: '降水量',
            type: 'bar',
            data: [
              2.6,
              5.9,
              9.0,
              26.4,
              28.7,
              70.7,
              175.6,
              182.2,
              48.7,
              18.8,
              6.0,
              2.3,
            ],
          },
          {
            name: '平均温度',
            type: 'line',
            yAxisIndex: 1,
            data: [
              2.0,
              2.2,
              3.3,
              4.5,
              6.3,
              10.2,
              20.3,
              23.4,
              23.0,
              16.5,
              12.0,
              6.2,
            ],
          },
        ],
      })
    },
  },
}
</script>
<style lang="scss" scoped>
.indexButton {
  box-sizing: border-box;
  width: 100%;
  height: 27%;
  margin-top: 0.5%;
  .indexButton_left {
    box-sizing: border-box;
    float: left;
    width: 20%;
    height: 100%;
    padding: 10px 15px;
    border: 2px solid skyblue;
    border-radius: 16px;
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
  .indexButton_between {
    box-sizing: border-box;
    float: left;
    width: 59%;
    height: 100%;
    padding: 10px 15px;
    margin: 0 0.5%;
    border: 2px solid skyblue;
    border-radius: 16px;
  }
  .indexButton_right {
    box-sizing: border-box;
    float: right;
    width: 20%;
    height: 100%;
    padding: 10px 15px;
    border: 2px solid skyblue;
    border-radius: 16px;
  }
}
</style>
