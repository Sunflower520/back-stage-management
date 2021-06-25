<template>
  <div id="app">
    <div id="nav">
      <router-view />
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
    };
  },
  methods: {
  },
};
</script>
<style lang="scss">
#app {
  width: 100%;
  height: 100%;
  #nav {
    width: 100%;
    height: 100%;
  }
}
</style>
