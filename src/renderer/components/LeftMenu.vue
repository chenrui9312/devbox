<template>
  <el-menu default-active="1-4-1" class="left-side-menu" @open="handleOpen" @close="handleClose" @select="handleSelect" :collapse="menuCollapse">
    <el-menu-item index="snippet">
      <i class="el-icon-document"></i>
      <span slot="title">代码片段</span>
    </el-menu-item>
    <el-menu-item index="exec">
      <i class="el-icon-edit"></i>
      <span slot="title">命令脚本</span>
    </el-menu-item>
    <el-menu-item index="tail">
      <i class="el-icon-view"></i>
      <span slot="title">日志监控</span>
    </el-menu-item>
    <el-menu-item index="proxy">
      <i class="el-icon-sort"></i>
      <span slot="title">代理抓包</span>
    </el-menu-item>
    <el-submenu index="tool">
      <template slot="title">
        <i class="el-icon-menu"></i>
        <span slot="title">常用工具</span>
      </template>
      <!-- <el-menu-item index="color-card">取色卡</el-menu-item> -->
      <el-submenu index="str">
        <span slot="title">文本处理</span>
        <el-menu-item index="str-encode">加密解密</el-menu-item>
        <el-menu-item index="str-diff">文本比较</el-menu-item>
        <el-menu-item index="str-qrcode">二维码生成</el-menu-item>
        <el-menu-item index="str-bejson">JSON校验</el-menu-item>
      </el-submenu>
      <el-submenu index="sys">
        <span slot="title">系统相关</span>
        <el-menu-item index="sys-process">系统进程</el-menu-item>
        <el-menu-item index="sys-portscan">端口扫描</el-menu-item>
        <el-menu-item index="sys-httpserver">HTTP服务</el-menu-item>
        <el-menu-item index="sys-ftpserver">FTP服务</el-menu-item>
      </el-submenu>
    </el-submenu>
    <el-menu-item index="settings">
      <i class="el-icon-setting"></i>
      <span slot="title">系统设置</span>
    </el-menu-item>
  </el-menu>
</template>

<script>
  import { mapState } from 'vuex'

  export default {
    computed: {
      ...mapState({
        menuCollapse: state => state.Settings.settings.menuCollapse || false
      })
    },
    methods: {
      handleOpen (key, keyPath) {
        console.log(key, keyPath)
      },
      handleClose (key, keyPath) {
        console.log(key, keyPath)
      },
      handleSelect (key, keyPath) {
        this.$store.dispatch('setNav', key)
        console.log(key, keyPath)
      }
    }
  }
</script>

<style>
.left-side-menu {
  min-height: 100%;
  /* min-width: 201px; */
  min-width: 100%;
  /* overflow: auto; */
}

.left-side-menu * {
  user-select: none;
}
</style>
