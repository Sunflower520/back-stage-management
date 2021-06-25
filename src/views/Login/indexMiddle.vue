<template>
  <div class="indexMiddle">
    <!-- 左侧 -->
    <div class="indexMiddle_left">
      <!-- 代办事项 -->
      <div class="Agent"></div>
      <!-- 玫瑰图表 -->
      <div class="roseChart"></div>
      <!-- 灌区概况 -->
      <div class="irrigatedSurvey">
        <el-table :data="tableData" border style="width: 100%" height="260">
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
    <div class="indexMiddle_right"></div>
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
  methods: {},
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
    }
    // 左侧-玫瑰图表
    .roseChart {
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
        color: #fff;
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
  }
}
</style>
