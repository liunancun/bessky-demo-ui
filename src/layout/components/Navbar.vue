<template>
  <div class="navbar">
    <!-- 导航栏 -->
    <div class="hamburger" @click="toggleSideBar">
      <!-- 汉堡包 -->
      <svg viewBox="0 0 1024 1024" xmlns="http://www.w3.org/2000/svg" width="64" height="64">
        <path
          d="M408 442h480c4.4 0 8-3.6 8-8v-56c0-4.4-3.6-8-8-8H408c-4.4 0-8 3.6-8 8v56c0 4.4 3.6 8 8 8zm-8 204c0 4.4 3.6 8 8 8h480c4.4 0 8-3.6 8-8v-56c0-4.4-3.6-8-8-8H408c-4.4 0-8 3.6-8 8v56zm504-486H120c-4.4 0-8 3.6-8 8v56c0 4.4 3.6 8 8 8h784c4.4 0 8-3.6 8-8v-56c0-4.4-3.6-8-8-8zm0 632H120c-4.4 0-8 3.6-8 8v56c0 4.4 3.6 8 8 8h784c4.4 0 8-3.6 8-8v-56c0-4.4-3.6-8-8-8zM142.4 642.1L298.7 519a8.84 8.84 0 0 0 0-13.9L142.4 381.9c-5.8-4.6-14.4-.5-14.4 6.9v246.3a8.9 8.9 0 0 0 14.4 7z"
        />
      </svg>
    </div>
    <el-breadcrumb separator="/">
      <el-breadcrumb-item>系统首页</el-breadcrumb-item>
      <el-breadcrumb-item>账号管理</el-breadcrumb-item>
      <el-breadcrumb-item>Lazada</el-breadcrumb-item>
      <el-breadcrumb-item>账号列表</el-breadcrumb-item>
    </el-breadcrumb>
    <el-dropdown trigger="click">
      <div class="avatar">
        <img src="https://wpimg.wallstcn.com/f778738c-e4f8-4870-b634-56703b4acafe.gif?imageView2/1/w/80/h/80" />
        <i class="el-icon-caret-bottom" />
      </div>
      <el-dropdown-menu slot="dropdown">
        <el-dropdown-item>Home</el-dropdown-item>
      </el-dropdown-menu>
    </el-dropdown>
  </div>
</template>

<script>
export default {
  name: 'Navbar',
  methods: {
    toggleSideBar() {
      this.$store.dispatch('toggleSideBar')
    }
  }
}
</script>

<style lang="scss" scoped>
.navbar {
  height: 50px;
  overflow: hidden;
  background: #fff;
  box-shadow: 0 1px 4px rgba(0, 21, 41, 0.08);

  .hamburger {
    line-height: 46px;
    height: 100%;
    float: left;
    cursor: pointer;
    padding: 0 15px;

    &:hover {
      background: rgba(0, 0, 0, 0.025);
    }

    svg {
      display: inline-block;
      vertical-align: middle;
      width: 20px;
      height: 20px;
      transform: rotate(180deg);
    }
  }

  .el-breadcrumb {
    display: inline-block;
    font-size: 14px;
    line-height: 50px;
    margin-left: 8px;
  }

  .el-dropdown {
    float: right;
    height: 100%;
    line-height: 50px;

    .avatar {
      margin-top: 5px;

      img {
        cursor: pointer;
        width: 40px;
        height: 40px;
        border-radius: 10px;
      }
    }
  }
}

.hide-sidebar .navbar .hamburger svg {
  transform: none;
}
</style>