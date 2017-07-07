<template>
  <div id="app">
    <!-- 头部导航 -->
    <header class="header">
      <el-row>
        <el-col :span="24">
          <el-menu theme="dark" :default-active="activeIndex" class="el-menu-demo" mode="horizontal"
                   @select="handleSelect">
            <el-menu-item class="logo-box" index="1">
              <img class="logo" src="./assets/logo.png">
            </el-menu-item>
            <div class="fr">
              <el-menu-item index="1" v-if="!hadLogin">登录</el-menu-item>
              <el-submenu index="2" v-if="hadLogin">
                <template slot="title">用户名：<span></span></template>
                <el-menu-item index="2-1">网站预览</el-menu-item>
                <el-menu-item index="2-2">退出登录</el-menu-item>
              </el-submenu>
              <el-menu-item index="3" v-if="!hadLogin">注册</el-menu-item>
            </div>
          </el-menu>
        </el-col>
      </el-row>
    </header>
    <main>
      <!-- 左侧导航 -->
      <div class="main-left">
        <h3>带 icon</h3>
        <el-menu theme="dark" default-active="2" class="el-menu-vertical-demo" @open="handleOpen" @close="handleClose">
          <el-submenu index="1">
            <template slot="title"><i class="el-icon-edit"></i>简介</template>
            <el-menu-item-group>
              <el-menu-item index="1-1">添加简介</el-menu-item>
              <el-menu-item index="1-2">修改简介</el-menu-item>
            </el-menu-item-group>
          </el-submenu>
          <el-submenu index="2">
            <template slot="title"><i class="el-icon-edit"></i>导航管理</template>
            <el-menu-item-group>
              <el-menu-item index="2-1">添加分类</el-menu-item>
              <el-menu-item index="2-2">分类列表</el-menu-item>
            </el-menu-item-group>
          </el-submenu>
          <el-submenu index="3">
            <template slot="title"><i class="el-icon-picture"></i>相册管理</template>
            <el-menu-item-group>
              <el-menu-item index="3-1">相册分类</el-menu-item>
              <el-menu-item index="3-2">添加分类</el-menu-item>
              <el-menu-item index="3-3">相册列表</el-menu-item>
              <el-menu-item index="3-4">添加相册</el-menu-item>
            </el-menu-item-group>
          </el-submenu>
          <el-submenu index="4">
            <template slot="title"><i class="el-icon-edit"></i>小视频管理</template>
            <el-menu-item-group>
              <el-menu-item index="4-1">小视频分类</el-menu-item>
              <el-menu-item index="4-2">添加分类</el-menu-item>
              <el-menu-item index="4-3">小视频列表</el-menu-item>
            </el-menu-item-group>
          </el-submenu>
          <el-submenu index="5">
            <template slot="title"><i class="el-icon-message"></i>生活记录</template>
            <el-menu-item-group>
              <el-menu-item index="5-1">分类列表</el-menu-item>
              <el-menu-item index="5-2">添加分类</el-menu-item>
              <el-menu-item index="5-3">文章列表</el-menu-item>
            </el-menu-item-group>
          </el-submenu>
          <el-submenu index="6">
            <template slot="title"><i class="el-icon-message"></i>其他</template>
            <el-menu-item-group>
              <el-menu-item index="6-1">分类列表</el-menu-item>
              <el-menu-item index="6-2">添加分类</el-menu-item>
              <el-menu-item index="6-3">内容列表</el-menu-item>
            </el-menu-item-group>
          </el-submenu>
        </el-menu>
      </div>

      <!-- 右侧主内容区 -->
      <div class="main-right">

      </div>
    </main>

    <router-view></router-view>
  </div>
</template>

<script>
  import Vue from 'vue'
  import ElementUI from 'element-ui'
  import 'element-ui/lib/theme-default/index.css'
  Vue.use(ElementUI)
  export default {
    name: 'app',
    data () {
      return {
        active: true,
        hadLogin: false
      }
    }
  }
</script>

<style>
  body {
    margin: 0;
  }

  .fr {
    float: right;
  }

  #app {
    min-width: 1200px;
    margin: 0 auto;
    font-family: "Helvetica Neue", "PingFang SC", Arial, sans-serif;
  }

  /* 头部导航 */
  header {
    z-index: 1000;
    position: fixed;
    left: 0;
    top: 0;
    width: 100%;
    min-width: 1200px;
  }

  header.header-fixed {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
  }

  header .logo-box {
    width: 200px;
    padding-top: 10px;
    height: 60px;
    line-height: 60px;
    text-align: center;
    background: rgba(0, 0, 0, .2);
  }

  header .logo {
    width: 40px;
    height: 40px;
    border-radius: 50%;
    background: rgba(255, 255, 255, .1);
  }

  header .el-menu-demo {
    float: right;
    width: 100%;
    text-align: right;
    padding-left: 20px !important;
  }

  .el-menu--horizontal > .el-menu-item:hover, .el-menu--horizontal > .el-submenu.is-active .el-submenu__title, .el-menu--horizontal > .el-submenu:hover .el-submenu__title {
    border-bottom: none;
  }

  /* 主内容区 */
  main {
    display: -webkit-box;
    display: -ms-flexbox;
    display: flex;
    min-height: 800px;
    padding-left: 200px;
    padding-top: 60px;
    background-color: #FCFCFC;
  }

  main .main-left {
    position: fixed;
    left: 0;
    top: 60px;
    width: 200px;
    min-height: 800px;
    overflow-y: auto;
    text-align: left;
    background: #324157;
  }

  main .main-left h3 {
    text-align: center;
    color: #fcfcfc;
  }

  main .main-right {
    -webkit-box-flex: 1;
    -ms-flex: 1;
    flex: 1;
    background-color: #fff;
    padding: 50px 70px;
  }
</style>
