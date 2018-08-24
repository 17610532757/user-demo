<template>
    <div class="my-main">
        <el-row>
            <el-col :span="8">
            <el-input v-model="inputUser" placeholder="请输入账号或用户名进行查询" :span="1"></el-input>
            </el-col>
            <el-col :span="2">
            <el-button @click="searchUser">查询</el-button>
            </el-col>
        </el-row>
        <el-table class="table"
    :data="tableData"  height="300"
    stripe
    style="width: 100%">
    <input type="checkbox"/>
    <el-table-column
      type="selection"
      width="55">
    </el-table-column>
    <el-table-column
      prop="date"
      label="账号"
      width="180">
    </el-table-column>   
    <el-table-column
      prop="name"
      label="姓名"
      width="180">
    </el-table-column>
    <el-table-column
      prop="password"
      label="密码">
    </el-table-column>
    <el-table-column
      prop="createtime"
      label="创建时间">
    </el-table-column>
    <el-table-column
      prop="email"
      label="邮箱">
    </el-table-column>
    <el-table-column
      prop="address"
      label="启动状态">
    </el-table-column>
    <el-table-column
      prop="address"
      label="安全级别">
    </el-table-column>
  </el-table>
    </div>
</template>

<script>
export default {
    name:'my-main',
    data(){
        return {
             tableData: [],
             inputUser:''
        }
    },
    methods:{
        searchUser:function(){
            var that = this;
            var filterdate = this.tableData.filter(function(value){
                return value.date == that.inputUser   ||    value.name == that.inputUser
            })
            this.tableData = filterdate
        }
    },
    created(){
        var that = this;
        this.$axios.get('http://api.haomo-studio.com/org/hm_users')
        .then(function (response) {
        console.log(response.data)
        var userInfo = response.data
        for(var i=0;i<userInfo.length;i++){
            that.tableData.push({
                date:userInfo[i].loginid,
                name:userInfo[i].username,
                address:1,
                password:userInfo[i].password,
                createtime:userInfo[i].createTime,
                email:userInfo[i].email
            })
        }
        
      })
    }
}
</script>

<style scoped>
.my-main{
    font-size:18px;
}
.my-main .table{
    font-size:10px;
    height: 200px;
}
</style>
