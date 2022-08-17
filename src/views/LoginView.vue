<template>
  <div class="login">
    <PageTitle msg="登录页" />
    <el-form ref="form" :model="form">
      <el-form-item label="账号" label-width="80px">
        <el-input placeholder="请输入内容" v-model="account" clearable>
        </el-input>
      </el-form-item>
      <el-form-item label="密码" label-width="80px">
        <el-input placeholder="请输入内容" v-model="password" clearable>
        </el-input>
      </el-form-item>
      <el-form-item>
        <el-button type="success" @click="login">登录</el-button>
      </el-form-item>
    </el-form>
  </div>
</template>

<script>
// @ is an alias to /src
import PageTitle from "@/components/PageTitle.vue";

export default {
  name: "LoginView",
  components: {
    PageTitle,
  },
  data() {
    return {
      account: "",
      password: "",
      verify: false,
    };
  },
  methods: {
    login() {
      if (this.account !== "" && this.password !== "") {
        this.verifysuccess();
        setTimeout(() => {
          location.href = "/";
        }, 1000);
      } else {
        this.verifyfail();
      }
    },
    verifysuccess() {
      this.$alert("即将跳转", "登录成功", {
        // confirmButtonText: "确定",
        // callback: (action) => {
        //   this.$message({
        //     type: "info",
        //     // message: `action: ${action}`,
        //   });
        // },
      });
    },
    verifyfail() {
      this.$alert("请输入正确的账号/密码", "验证失败", {
        confirmButtonText: "返回",
        // callback: (action) => {
        //   this.$message({
        //     type: "info",
        //     // message: `action: ${action}`,
        //   });
        // },
      });
    },
  },
};
</script>
<style lang="less" scoped>
.login {
  margin-top: 34vh;
}
.el-form {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>