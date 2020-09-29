<!--
 * @Author: your name
 * @Date: 2020-09-26 14:20:36
 * @LastEditTime: 2020-09-29 15:42:12
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: /vue3-project/src/views/layout/menu.vue
-->
<template>
  <a-menu
    :inlineCollapsed="true"
    theme="dark"
    mode="inline"
    v-model:openKeys="openKeys"
    v-model:selectedKeys="selectedKeys"
  >
    <a-menu-item key="/home">
      <router-link to="/home">home </router-link>
    </a-menu-item>

    <a-sub-menu key="sub2" @titleClick="titleClick">
      <template v-slot:title>
        <span> <AppstoreOutlined /><span>信息</span> </span>
      </template>
      <a-menu-item key="/goods/list">
        <router-link to="/goods/list">列表 </router-link>
      </a-menu-item>
      <a-menu-item key="/goods/about">
        <router-link to="/goods/about">详情 </router-link>
      </a-menu-item>

      <a-sub-menu key="sub3" title="Submenu">
        <a-menu-item key="/goods/list">
          <router-link to="/goods/list">列表1 </router-link>
        </a-menu-item>
        <a-menu-item key="/goods/about">
          <router-link to="/goods/about">详情1 </router-link>
        </a-menu-item>
      </a-sub-menu>
    </a-sub-menu>
  </a-menu>
</template>

<script>
import { toRefs, reactive, watch, watchEffect, computed } from "vue";
import { useRoute, onBeforeRouteUpdate } from "vue-router";
import { useStore } from "vuex";

export default {
  setup(props) {
    const route = useRoute();
    const store = useStore();
    const state = reactive({
      selectedKeys: computed(() => [store.getters.GET_ACTIVE_ROUTER]),
      openKeys: ["sub2", "sub3"],
    });

    return {
      ...toRefs(state),
    };
  },
};
</script>

<style >
</style>
