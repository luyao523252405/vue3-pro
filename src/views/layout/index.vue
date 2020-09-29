<!--
 * @Author: your name
 * @Date: 2020-09-26 14:03:27
 * @LastEditTime: 2020-09-29 19:20:08
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: /vue3-project/src/views/layout/index.vue
-->
<template>
  <a-layout id="components-layout-demo-custom-trigger">
    <a-layout-sider v-model:collapsed="collapsed" :trigger="null" collapsible>
      <div class="logo">荡啊荡</div>
      <menus />
    </a-layout-sider>
    <a-layout>
      <a-layout-header style="background: #fff; padding: 0">
        <menu-unfold-outlined
          v-if="collapsed"
          class="trigger"
          @click="() => (collapsed = !collapsed)"
        />
        <menu-fold-outlined
          v-else
          class="trigger"
          @click="() => (collapsed = !collapsed)"
        />
        <loginOut />
      </a-layout-header>
      <a-layout-content
        :style="{
          margin: '24px 16px',
          padding: '24px',
          background: '#fff',
          minHeight: '280px',
        }"
      >
        <router-view />
      </a-layout-content>
    </a-layout>
  </a-layout>
</template>

<script>
import {
  UserOutlined,
  VideoCameraOutlined,
  UploadOutlined,
  MenuUnfoldOutlined,
  MenuFoldOutlined,
} from "@ant-design/icons-vue";

import menus from "./menu";
import loginOut from "./components/loginOut";

export default {
  components: {
    UserOutlined,
    VideoCameraOutlined,
    UploadOutlined,
    MenuUnfoldOutlined,
    MenuFoldOutlined,
    menus,
    loginOut,
  },
  data() {
    return {
      selectedKeys: ["1"],
      collapsed: false,
    };
  },
};
</script>

<style lang="less" scoped>
#components-layout-demo-custom-trigger {
  height: 100vh;
  width: 100vw;
}

#components-layout-demo-custom-trigger .trigger {
  font-size: 18px;
  line-height: 64px;
  padding: 0 24px;
  cursor: pointer;
  transition: color 0.3s;
}

#components-layout-demo-custom-trigger .trigger:hover {
  color: #1890ff;
}

#components-layout-demo-custom-trigger .logo {
  height: 64px;
  line-height: 64px;
  color: white;
  text-align: center;
  font-size: 20px;
  background: rgba(255, 255, 255, 0.2);
  //   margin: 16px;
}
</style>
