<template>
  <div class="home">
    <el-tabs v-model="activeName" type="card" @tab-click="handleClick">
      <el-tab-pane label="登录" name="first"><SignIn /></el-tab-pane>
      <el-tab-pane label="注册" name="second"><register /></el-tab-pane>
    </el-tabs>
  </div>
</template>
<script>
import SignIn from "./SignIn";
import register from "./register";
export default {
  components: {
    SignIn,
    register,
  },
  data() {
    return {
      activeName: "first",
    };
  },
  methods: {
    handleClick(tab, event) {
      console.log(tab, event);
    },
  },
};
</script>
<style lang="scss" scoped>
.home {
  margin-top: 10vh;
  /deep/ .el-tabs__header {
    border-bottom: none;
    .el-tabs__nav {
      margin-left: 50%;
      transform: translate(-50%, 0) !important;
      border-bottom: none;
      .el-tabs__item {
        font-size: 20px;
      }
    }
  }
  /deep/ .el-tabs__content {
    text-align: center;
  }
}
</style>