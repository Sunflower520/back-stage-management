<template>
  <div class="indexTop">
    <!-- 顶部按钮标题 -->
    <div class="menuButton">
      <el-badge :value="12" class="item">
        <el-button size="small">灌区大图</el-button>
      </el-badge>
      <el-badge :value="12" class="item">
        <el-button>数据采集</el-button>
      </el-badge>
      <el-badge :value="12" class="item">
        <el-button>应急管理</el-button>
      </el-badge>
      <el-badge :value="12" class="item">
        <el-button>数字移交</el-button>
      </el-badge>
      <h1>灌区BIM运维综合信息系统</h1>
      <el-badge :value="12" class="item">
        <el-button>统计发布</el-button>
      </el-badge>
      <el-badge :value="12" class="item">
        <el-button>智慧运营</el-button>
      </el-badge>
      <el-badge :value="12" class="item">
        <el-button>以电折水</el-button>
      </el-badge>
      <el-badge :value="12" class="item">
        <el-button>系统管理</el-button>
      </el-badge>
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
      <transition name="fade">
        <div class="wrapTwo">
          <div class="fatherTwo">
            <noticebar :options="options"></noticebar>
          </div>
        </div>
      </transition>
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
        // icon:
        //   'https://ss0.bdstatic.com/70cFvHSh_Q1YnxGkpoWK1HF6hhy/it/u=735421754,4062673022&fm=26&gp=0.jpg', // 左侧图标(不需要icon不传)
        // iconSize: '16px', // icon大小（正方形默认16px）
        size: '16px', // 通知内容文字大小（默认16px）
        color: 'red', // 通知内容文字颜色(默认#f60)
        backround: 'rgb(5, 14, 59)', //背景颜色(默认#fff7cc)
        delay: '1000', // 动画延迟时间(默认一秒后开始滚动，单位毫秒)
        speed: '50', // 滚动速率默认50 (px/s)
      },
      options: {
        text: '欢迎管理员XXX登录上线',
        // icon:
        //   'https://ss0.bdstatic.com/70cFvHSh_Q1YnxGkpoWK1HF6hhy/it/u=735421754,4062673022&fm=26&gp=0.jpg', // 左侧图标(不需要icon不传)
        // iconSize: '16px', // icon大小（正方形默认16px）
        size: '16px', // 通知内容文字大小（默认16px）
        color: '#fff', // 通知内容文字颜色(默认#f60)
        backround: 'rgb(5, 14, 59)', //背景颜色(默认#fff7cc)
        delay: '1000', // 动画延迟时间(默认一秒后开始滚动，单位毫秒)
        speed: '50', // 滚动速率默认50 (px/s)
      },
    }
  },
  methods: {},
}
</script>
<style lang="scss" scoped>
.menuButton {
  display: flex;
  h1 {
    margin: 0 100px;
    color: #fff;
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
      border: 2px solid skyblue;
      background: transparent;
      border-radius: 20px;
    }
    .el-button:focus,
    .el-button:hover {
      color: #ccc !important;
    }
    .el-badge__content.is-fixed {
      right: 76px;
    }
  }
}
.noticebars {
  overflow: hidden;
  border-top: 2px solid skyblue;
  margin-top: 1%;
  margin-bottom: 10px;
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
