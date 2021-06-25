<template>
  <div class="home">
    <indexTop />
    <indexMiddle />
    <indexBottom />
  </div>
</template>
<script>
import indexTop from './indexTop'
import indexMiddle from './indexMiddle'
import indexBottom from './indexBottom'

export default {
  components: {
    indexTop,
    indexMiddle,
    indexBottom,
  },
  data() {
    return {}
  },
  methods: {},
}
</script>
<style lang="scss" scoped>
.home {
  box-sizing: border-box;
  width: 100%;
  height: 100vh;
  background-color: rgb(5, 14, 59);
  padding: 10px;
}
</style>
