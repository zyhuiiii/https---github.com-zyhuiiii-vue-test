<template>
  <div class="home">
    <el-container>
      <!-- 侧边栏 -->
      <el-aside width="20vw">
        <PageTitle msg="首页" />
        <!-- 侧边菜单 -->
        <el-row class="tac">
          <el-col>
            <h5>默认颜色</h5>
            <el-menu
              default-active="2"
              class="el-menu-vertical-demo"
              @open="handleOpen"
              @close="handleClose"
            >
              <el-submenu index="1">
                <template slot="title">
                  <i class="el-icon-location"></i>
                  <span>导航一</span>
                </template>
                <el-menu-item-group>
                  <template slot="title">分组一</template>
                  <el-menu-item index="1-1">选项1</el-menu-item>
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
        </el-row>
      </el-aside>
      <el-container>
        <!-- 头部栏 -->
        <el-header>
          <!-- 用户信息 -->
          <div class="demo-type">
            <!-- 用户头像 -->
            <div>
              <el-avatar
                src="https://www.creativebio.cn/Statics/klm/img/preloader.gif"
              ></el-avatar>
            </div>
          </div>
          你好，
          <div class="username">{{ user }}！</div>
          <!-- 返回键 -->
          <button class="logoff" @click="goback">注销</button>
        </el-header>
        <!-- 主要内容 -->
        <el-main>
          <!-- 面包屑 -->
          <el-breadcrumb separator="/">
            <el-breadcrumb-item :to="{ path: '/' }">首页</el-breadcrumb-item>
            <el-breadcrumb-item><a href="/">活动管理</a></el-breadcrumb-item>
            <el-breadcrumb-item><a href="/">活动列表</a></el-breadcrumb-item>
            <el-breadcrumb-item>活动详情</el-breadcrumb-item>
          </el-breadcrumb>
        </el-main>
      </el-container>
    </el-container>
  </div>
</template>

<script>
// @ is an alias to /src
import PageTitle from "@/components/PageTitle.vue";

export default {
  name: "HomeView",
  data() {
    return {
      user: "用户1",
    };
  },
  components: {
    PageTitle,
  },
  methods: {
    goback() {
      // this.$router.go(-1);//返回上一页
      this.$router.push("/login"); //跳转至路由页
    },
  },
};
</script>

<style lang="less" scoped>
.logoff {
  margin-right: 10px;
}
.el-header,
.el-aside,
.el-main {
  border: 1px solid #ccc;
  padding: 0;
}
.el-header {
  display: flex;
  justify-content: flex-end;
  align-items: center;
}
.el-breadcrumb {
  padding: 10px;
  border-bottom: 1px solid #ccc;
}
.el-aside {
  height: 98vh;
}
</style>