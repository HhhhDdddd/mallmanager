<template>
    <div class="login-wrap">
        <el-form class="login-form" label-position=top label-width="80px" :model="formData">
            <h2>用户登录</h2>
            <el-form-item label="用户名">
                <el-input v-model="formData.username"></el-input>
            </el-form-item>
            <el-form-item label="密码">
                <el-input v-model="formData.password"></el-input>
            </el-form-item>
            <el-button type="primary" class="login-button" @click.prevent="handleLogin()">登录</el-button>
        </el-form>
    </div>
</template>

<script>
export default {
  data() {
    return {
      labelPosition: "",
      formData: {
        username: "",
        password: ""
      }
    };
  },
  methods: {
    async handleLogin() {
      const res = await this.$http.post("login", this.formData);
      // console.log(res.data)
      const {
        data,
        meta: { status, msg }
      } = res.data;
      if (status == 200) {
        localStorage.setItem("token", data.token);
        this.$message.success("登录成功");
        this.$router.push({ name: "home" });
      } else {
        this.$message.warning(msg);
      }
    }
  }
};
</script>

<style>
.login-wrap {
  background-color: steelblue;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}
.login-wrap h2 {
  color: steelblue;
}
.login-wrap .login-form {
  width: 300px;
  /* height: 300px; */
  padding: 30px;
  border-radius: 5px;
  background: #fff;
  color: #fff;
}
.login-wrap .login-button {
  width: 100%;
}
</style>
