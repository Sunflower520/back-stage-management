<template>
  <div class="indexTop">
    <!-- 顶部按钮标题 -->
    <div class="menuButton">
      <h1>
        <img
          src="../../../src/assets/main_logo.png"
          alt=""
          style="width: 36px; display: inline-block; vertical-align: middle"
        />
        灌区BIM运维综合信息系统
      </h1>
      <el-badge class="item">
        <el-button size="small">
          <img src="../../../src/assets/icon1.png" alt="" style="width: 26px; margin-bottom: 4px;display: inline-block; vertical-align: middle">
          <!-- <i
            class="el-icon-menu"
            style="font-size: 24px; margin-bottom: 2px; color: skyblue"
          ></i> -->
          <p style="color: skyblue">灌区一大图</p></el-button
        >
      </el-badge>
      <el-badge class="item">
        <el-button>
          <img src="../../../src/assets/icon2.png" alt="" style="width: 26px; margin-bottom: 4px;display: inline-block; vertical-align: middle">
          <!-- <i
            class="el-icon-s-claim"
            style="font-size: 24px; margin-bottom: 2px; color: skyblue"
          ></i> -->
          <p style="color: skyblue">数据采集</p>
        </el-button>
      </el-badge>
      <el-badge class="item">
        <el-button>
          <img src="../../../src/assets/icon3.png" alt="" style="width: 26px; margin-bottom: 4px;display: inline-block; vertical-align: middle">
          <!-- <i
            class="el-icon-warning-outline"
            style="font-size: 24px; margin-bottom: 2px; color: skyblue"
          ></i> -->
          <p style="color: skyblue">应急管理</p></el-button
        >
      </el-badge>
      <el-badge class="item">
        <el-button>
          <img src="../../../src/assets/icon4.png" alt="" style="width: 26px; margin-bottom: 4px;display: inline-block; vertical-align: middle">
          <!-- <i
            class="el-icon-document-copy"
            style="font-size: 24px; margin-bottom: 2px; color: skyblue"
          ></i> -->
          <p style="color: skyblue">数字移交</p></el-button
        >
      </el-badge>
      <el-badge class="item">
        <el-button>
          <img src="../../../src/assets/icon5.png" alt="" style="width: 26px; margin-bottom: 4px;display: inline-block; vertical-align: middle">
          <!-- <i
            class="el-icon-s-marketing"
            style="font-size: 24px; margin-bottom: 2px; color: skyblue"
          ></i> -->
          <p style="color: skyblue">综合监管</p></el-button
        >
      </el-badge>
      <el-badge class="item">
        <el-button>
          <img src="../../../src/assets/icon6.png" alt="" style="width: 26px; margin-bottom: 4px;display: inline-block; vertical-align: middle">
          <!-- <i
            class="el-icon-s-tools"
            style="font-size: 24px; margin-bottom: 2px; color: skyblue"
          ></i> -->
          <p style="color: skyblue">智慧运营</p></el-button
        >
      </el-badge>
      <el-badge class="item">
        <el-button>
          <img src="../../../src/assets/icon7.png" alt="" style="width: 26px; margin-bottom: 4px;display: inline-block; vertical-align: middle">
          <!-- <i
            class="el-icon-s-opportunity"
            style="font-size: 24px; margin-bottom: 2px; color: skyblue"
          ></i> -->
          <p style="color: skyblue">以电折水</p></el-button
        >
      </el-badge>
      <el-badge class="item">
        <el-button>
          <img src="../../../src/assets/icon8.png" alt="" style="width: 26px; margin-bottom: 4px;display: inline-block; vertical-align: middle">
          <!-- <i
            class="el-icon-monitor"
            style="font-size: 24px; margin-bottom: 2px; color: skyblue"
          ></i> -->
          <p style="color: skyblue">系统管理</p></el-button
        >
      </el-badge>
    </div>
    <div class="logOut">
      <el-badge :value="12" class="item">
        <i class="el-icon-bell" style="color: skyblue; font-size: 20px"></i>
      </el-badge>
      <span style="margin-left: 30px">欢迎</span>&nbsp;&nbsp;&nbsp;&nbsp;<span
        >管理员!</span
      >
      <el-button>
        <i class="el-icon-edit" style="color: skyblue"></i>
        退出登录</el-button
      >
    </div>
    <!-- 滚动条 -->
    <div class="noticebars">
      <transition name="fade">
        <div class="wrapOne">
          <div class="fatherOne">
            <noticebar :options="optionsOne"></noticebar>
          </div>
        </div>
      </transition>
      <!-- <transition name="fade">
        <div class="wrapTwo">
          <div class="fatherTwo">
            <noticebar :options="options"></noticebar>
          </div>
        </div>
      </transition> -->
    </div>
  </div>
</template>
<script>
import noticebar from '../../components/NoticeBar' // 引入滚动播放提示条组件
export default {
  components: {
    noticebar,
  },
  data() {
    return {
      optionsOne: {
        text: '通知:监测预警，双鹤灌区水位已到达11CM',
        icon: 'el-icon-bell', // 左侧图标(不需要icon不传)
        iconSize: '16px', // icon大小（正方形默认16px）
        size: '16px', // 通知内容文字大小（默认16px）
        color: 'red', // 通知内容文字颜色(默认#f60)
        backround: 'rgb(5, 14, 59)', //背景颜色(默认#fff7cc)
        delay: '1000', // 动画延迟时间(默认一秒后开始滚动，单位毫秒)
        speed: '50', // 滚动速率默认50 (px/s)
      },
      // options: {
      //   text: '欢迎管理员XXX登录上线',
      //   // icon:
      //   //   'https://ss0.bdstatic.com/70cFvHSh_Q1YnxGkpoWK1HF6hhy/it/u=735421754,4062673022&fm=26&gp=0.jpg', // 左侧图标(不需要icon不传)
      //   // iconSize: '16px', // icon大小（正方形默认16px）
      //   size: '16px', // 通知内容文字大小（默认16px）
      //   color: '#fff', // 通知内容文字颜色(默认#f60)
      //   backround: 'rgb(5, 14, 59)', //背景颜色(默认#fff7cc)
      //   delay: '1000', // 动画延迟时间(默认一秒后开始滚动，单位毫秒)
      //   speed: '50', // 滚动速率默认50 (px/s)
      // },
    }
  },
  methods: {},
}
</script>
<style lang="scss" scoped>
.menuButton {
  float: left;
  width: 84%;
  h1 {
    float: left;
    margin-right: 70px;
    color: skyblue;
    font-weight: 600;
    font-size: 22px;
  }
  /deep/ .el-badge {
    flex: 1;

    /deep/.el-button {
      // justify-content:space-between;
      padding: 5px 10px;
      margin: 0 30px !important;
      color: #fff !important;
      border: none;
      background: transparent;
      border-radius: 20px;
    }
    // .el-button:hover,
    // i:hover,
    // p:hover {
    //   color: #ccc !important;
    // }
    .el-badge__content.is-fixed {
      right: 76px;
    }
  }
}
.logOut {
  float: right;
  width: 16%;
  span {
    color: skyblue;
  }
  /deep/.el-button {
    // justify-content:space-between;
    padding: 5px 10px;
    margin-left: 40px !important;
    color: skyblue !important;
    border: 2px solid skyblue;
    background: transparent;
    border-radius: 20px;
  }
}
.noticebars {
  width: 100%;
  overflow: hidden;
  border-top: 2px solid skyblue;
  // margin-top: 1%;
  // margin-bottom: 10px;
  .wrapOne {
    .fatherOne {
      //   margin: 150px auto;
      float: left;
      margin-left: 33%;
      width: 30%;
      height: 24px;
      //   img {
      //     width: 20px;
      //     height: 100%;
      //   }
    }
  }
  .wrapTwo {
    .fatherTwo {
      //   margin: 150px auto;
      float: right;
      margin-left: 1%;
      width: 30%;
      height: 24px;
      //   img {
      //     width: 20px;
      //     height: 100%;
      //   }
    }
  }
}
</style>
