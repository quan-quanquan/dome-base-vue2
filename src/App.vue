<template>
  <div id="app">
    <el-menu class="nav" mode="horizontal">
      <el-menu-item index="1">
        <router-link to="/big-file-upload">大文件上传</router-link>
      </el-menu-item>
      <el-menu-item index="2">
        <router-link to="/directives">自定义指令</router-link>
      </el-menu-item>
    </el-menu>
    <router-view></router-view>
  </div>
</template>

<script>


export default {
  name: 'App',
  components: {
  },
  data() {
    return {
    }
  },
  mounted() {
    
  }
}
</script>

<style lang="less" scoped>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  a {
    text-decoration: none;
  }
  .nav {
    margin-bottom: 24px;
  }
}
</style>
