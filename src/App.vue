<template>
  <!--  <nav>-->
  <!--    <router-link to="/">Home</router-link> |-->
  <!--    <router-link to="/about">About</router-link>-->
  <!--  </nav>-->
  <router-view/>
</template>

<script>
import {provide} from "vue"
import * as echarts from "echarts"
import axios from "axios"
// import mysql from "mysql"

// axios.defaults.baseURL = "http://localhost:8989"
axios.defaults.baseURL = "https://aws.jianghuan.top/bi_data"

export default {
  setup() {
    provide("echarts", echarts)
    provide("axios", axios)
    // provide("mysql", mysql)
  }
}
</script>

<style lang="less">
body {
  background: url("~@/assets/background.png") top center no-repeat;
}

* {
  margin: 0px;
  padding: 0px;
  box-sizing: border-box;
}

//#app {
//  font-family: Avenir, Helvetica, Arial, sans-serif;
//  -webkit-font-smoothing: antialiased;
//  -moz-osx-font-smoothing: grayscale;
//  text-align: center;
//  color: #2c3e50;
//}
//
//nav {
//  padding: 30px;
//
//  a {
//    font-weight: bold;
//    color: #2c3e50;
//
//    &.router-link-exact-active {
//      color: #42b983;
//    }
//  }
//}
</style>
