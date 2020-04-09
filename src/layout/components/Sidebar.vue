<template>
  <div class="sidebar" :class="{'has-logo':showLogo}">
    <!-- 侧边栏 -->
    <div v-if="showLogo" class="logo">
      <!-- Logo -->
      <a>
        <img src="https://wpimg.wallstcn.com/69a1c46c-eb1c-4b46-8bd4-e9e686ef5251.png" />
        <h1 v-if="!isCollapse">后台管理系统</h1>
      </a>
    </div>
    <el-scrollbar>
      <el-menu :collapse="isCollapse" background-color="#304156" text-color="#bfcbd9" active-text-color="#409EFF">
        <template v-for="first in items">
          <el-menu-item :key="first.index" :index="first.index" v-if="!first.children">
            <i v-if="first.icon" :class="first.icon"></i>
            <span>{{first.title}}</span>
          </el-menu-item>
          <el-submenu :key="first.index" :index="first.index" v-if="first.children">
            <template slot="title">
              <i v-if="first.icon" :class="first.icon"></i>
              <span>{{first.title}}</span>
            </template>
            <template v-for="second in first.children">
              <el-menu-item :key="second.index" :index="second.index" v-if="!second.children">
                <span>{{second.title}}</span>
              </el-menu-item>
              <el-submenu :key="second.index" :index="second.index" v-if="second.children">
                <template slot="title">
                  <span>{{second.title}}</span>
                </template>
                <template v-for="third in second.children">
                  <el-menu-item :key="third.index" :index="third.index" v-if="!third.children">
                    <span>{{third.title}}</span>
                  </el-menu-item>
                </template>
              </el-submenu>
            </template>
          </el-submenu>
        </template>
      </el-menu>
    </el-scrollbar>
  </div>
</template>

<script>
import { mapGetters } from 'vuex'

export default {
  name: 'Sidebar',
  data() {
    return {
      showLogo: true,
      items: [
        {
          index: 'home',
          title: '系统首页',
          icon: 'el-icon-s-home'
        },
        {
          index: 'account',
          title: '账号管理',
          icon: 'el-icon-user',
          children: [
            {
              index: 'account/amazon',
              title: 'Amazon'
            },
            {
              index: 'account/lazada',
              title: 'Lazada'
            },
            {
              index: 'account/lazada1',
              title: 'Lazada1'
            },
            {
              index: 'account/lazada2',
              title: 'Lazada2'
            },
            {
              index: 'account/lazada3',
              title: 'Lazada3'
            },
            {
              index: 'account/lazada4',
              title: 'Lazada4'
            },
            {
              index: 'account/lazada5',
              title: 'Lazada5'
            },
            {
              index: 'account/lazada6',
              title: 'Lazada6'
            },
            {
              index: 'account/lazada7',
              title: 'Lazada7'
            },
            {
              index: 'account/lazada8',
              title: 'Lazada8'
            },
            {
              index: 'account/lazada9',
              title: 'Lazada9'
            }
          ]
        },
        {
          index: 'order',
          title: '订单管理',
          icon: 'el-icon-goods',
          children: [
            {
              index: 'order/amazon',
              title: 'Amazon'
            },
            {
              index: 'order/lazada',
              title: 'Lazada'
            }
          ]
        },
        {
          index: 'product',
          title: '产品管理',
          icon: 'el-icon-eleme',
          children: [
            {
              index: 'product/amazon',
              title: 'Amazon',
              children: [
                {
                  index: 'product/amazon/template',
                  title: '刊登模板'
                },
                {
                  index: 'product/amazon/product',
                  title: '在线列表'
                }
              ]
            },
            {
              index: 'product/lazada',
              title: 'Lazada'
            }
          ]
        }
      ]
    }
  },
  computed: {
    ...mapGetters(['sidebar']),
    isCollapse() {
      return !this.sidebar.opened
    }
  }
}
</script>

<style lang="scss" scoped>
.sidebar {
  transition: width 0.28s;
  width: 210px;
  background-color: #304156;
  height: 100%;
  position: fixed;
  top: 0;
  bottom: 0;
  left: 0;

  .logo {
    height: 50px;
    line-height: 50px;
    background: #2b2f3a;
    text-align: center;

    img {
      width: 32px;
      height: 32px;
      vertical-align: middle;
      margin-right: 12px;
    }

    h1 {
      display: inline-block;
      margin: 0;
      color: #fff;
      font-weight: 600;
      line-height: 50px;
      font-size: 14px;
      font-family: Avenir, Helvetica Neue, Arial, Helvetica, sans-serif;
      vertical-align: middle;
    }
  }

  ::v-deep .el-scrollbar {
    height: 100%;

    .el-scrollbar__wrap {
      overflow-x: hidden;
    }
  }

  ::v-deep .el-menu {
    border: none;
    height: 100%;

    .el-submenu__title {
      &:hover {
        background-color: #263445 !important;
      }
    }

    .el-submenu {
      .el-submenu .el-submenu__title,
      .el-menu-item {
        background-color: #1f2d3d !important;

        &:hover {
          background-color: #001528 !important;
        }
      }
    }

    .is-active > .el-submenu__title {
      color: #f4f4f5 !important;
    }
  }
}

.has-logo .el-scrollbar {
  height: calc(100% - 50px);
}

.hide-sidebar .sidebar {
  width: 64px;

  .logo img {
    margin-right: 0px;
  }
}
</style>