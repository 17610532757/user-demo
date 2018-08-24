<template>
  <div id="app">
      <myheader></myheader>
      <mycontainer></mycontainer>
    <router-view/>
  </div>
</template>

<script>
import mycontainer from "./components/myContainer"
import myheader from "./components/myHeader"

export default {
  name: 'App',
  components:{
    mycontainer,myheader
  }
}
</script>

<style>
html,body{
  padding: 0;
  margin: 0;
  list-style: none;
}
</style>
