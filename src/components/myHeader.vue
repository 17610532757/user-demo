<template>
  <div class="myheader">
    <el-menu class="el-menu-demo" mode="horizontal">
  <el-menu-item index="1"> 鸿合业务协作系统后台</el-menu-item>
  <el-menu-item index="3" disabled>默认管理员</el-menu-item>
</el-menu>
  </div>
</template>

<script>
export default {
  name: 'myheader',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.el-menu-demo{
  background: #363d4c;
}
</style>
