<template>
    <div class="container">
        <el-row class="tac">
  <el-col :span="4">
    <el-menu
      default-active="2"
      class="el-menu-vertical-demo"
     >
      <el-submenu index="1">
        <template slot="title">
          <i class="el-icon-location"></i>
          <span>用户权限管理</span>
        </template>
        <el-menu-item-group>
          <el-menu-item index="1-1" @click="linkto">用户管理</el-menu-item>
          <el-menu-item index="1-2">选项2</el-menu-item>
        </el-menu-item-group>
        <el-menu-item-group title="分组2">
          <el-menu-item index="1-3">选项3</el-menu-item>
        </el-menu-item-group>
        <el-submenu index="1-4">
          <template slot="title">选项4</template>
          <el-menu-item index="1-4-1">选项1</el-menu-item>
        </el-submenu>
      </el-submenu>
      <el-menu-item index="2">
        <i class="el-icon-menu"></i>
        <span slot="title">导航二</span>
      </el-menu-item>
      <el-menu-item index="3" disabled>
        <i class="el-icon-document"></i>
        <span slot="title">导航三</span>
      </el-menu-item>
      <el-menu-item index="4">
        <i class="el-icon-setting"></i>
        <span slot="title">导航四</span>
      </el-menu-item>
    </el-menu>
  </el-col>
  <el-col :span="5">
      <el-tree :data="date"></el-tree>
  </el-col>
  <el-col :span="14" class="main-right">
  <my-main></my-main>
  </el-col>
  </el-row>
    </div>
</template>

<script>

import myMain from "./myMain"

export default {
    name:'container',
    components:{
      myMain
    },
    data(){
        return{
            date: [],
        }
    },
    methods:{
        linkto:function (){
            this.$router.push('myMain')
        }
    },
    created(){
      var that = this;
      this.$axios.get('http://api.haomo-studio.com/org/departments')
      .then(function (response) {      
        var arr = response.data;
        for(var i=0;i<arr.length;i++){
          that.date.push({label:arr[i].name,children:[{label:1}]})
        }
      })
    }
}
</script>

<style scoped>

</style>


