<template>
  <el-container class="container">
    <el-header class="header">
      <el-row>
        <el-col :span="4">
          <div class="grid-content bg-purple">
            <img src="../../assets/logo.png" alt srcset>
          </div>
        </el-col>
        <el-col :span="18" class="middle">
          <h1>电商后台管理系统</h1>
        </el-col>
        <el-col :span="2">
          <a href="javascript:;" class="loginout" @click.prevent="loginout()">退出</a>
        </el-col>
      </el-row>
    </el-header>
    <el-container>
      <el-aside width="200px" class="aside">
        <el-menu unique-opened=true router=true>
          <el-submenu index="1">
            <template slot="title">
              <i class="el-icon-location"></i>
              <span>用户管理</span>
            </template>
            <el-menu-item-group>
              <el-menu-item index="/users">
                <i class="el-icon-location"></i>
                用户列表
              </el-menu-item>
            </el-menu-item-group>
          </el-submenu>
          <el-submenu index="2">
            <template slot="title">
              <i class="el-icon-location"></i>
              <span>权限管理</span>
            </template>
            <el-menu-item-group>
              <el-menu-item index="1-1">
                <i class="el-icon-location"></i>
                角色列表
              </el-menu-item>
              <el-menu-item index="1-1">
                <i class="el-icon-location"></i>
                权限列表
              </el-menu-item>
            </el-menu-item-group>
          </el-submenu>

          <el-submenu index="3">
            <template slot="title">
              <i class="el-icon-location"></i>
              <span>商品管理</span>
            </template>
            <el-menu-item-group>
              <el-menu-item index="1-1">
                <i class="el-icon-location"></i>
                商品列表
              </el-menu-item>
              <el-menu-item index="1-1">
                <i class="el-icon-location"></i>
                分类参数
              </el-menu-item>
              <el-menu-item index="1-1">
                <i class="el-icon-location"></i>
                商品分类
              </el-menu-item>
            </el-menu-item-group>
          </el-submenu>
          <el-submenu index="4">
            <template slot="title">
              <i class="el-icon-location"></i>
              <span>订单管理</span>
            </template>
            <el-menu-item-group>
              <el-menu-item index="1-1">
                <i class="el-icon-location"></i>
                订单列表
              </el-menu-item>
            </el-menu-item-group>
          </el-submenu>
          <el-submenu index="5">
            <template slot="title">
              <i class="el-icon-location"></i>
              <span>数据统计</span>
            </template>
            <el-menu-item-group>
              <el-menu-item index="1-1">
                <i class="el-icon-location"></i>
                数据报表
              </el-menu-item>
            </el-menu-item-group>
          </el-submenu>
        </el-menu>
      </el-aside>
      <el-main class="main">
          <router-view></router-view>
      </el-main>
    </el-container>
  </el-container>
</template>

<script>
    export default {
    
        beforeCreate() {
    
            var token = localStorage.getItem("token");
    
            if (!token) {
    
                this.$router.push({
    
                    name: "login"
    
                });
    
            }
    
        },
    
        methods: {
    
            loginout() {
    
                localStorage.clear();
    
                this.$message.success("退出成功");
    
                this.$router.push({
    
                    name: "login"
    
                });
    
            }
    
        }
    
    };
</script>

<style>
    .container {
    
        height: 100%;
    
    }
    
    
    
    .header {
    
        background-color: #b3c0d1;
    
    }
    
    
    
    .aside {
    
        background-color: #d3dce6;
    
    }
    
    
    
    .main {
    
        background-color: #e9eef3;
    
        /* height: 100%; */
    
    }
    
    
    
    .middle {
    
        text-align: center;
    
    }
    
    
    
    .loginout {
    
        line-height: 60px;
    
        text-decoration: none;
    
    }
</style>
