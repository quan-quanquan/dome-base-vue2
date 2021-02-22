<template>
  <div id="app">
    <el-menu mode="horizontal">
      <el-menu-item index="1">
        <router-link to="/big-file-uploader">大文件上传</router-link>
      </el-menu-item>
    </el-menu>
    <router-view/>
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
}
</style>
