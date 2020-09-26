<!--
 * @Author: your name
 * @Date: 2020-09-26 14:20:36
 * @LastEditTime: 2020-09-26 16:23:22
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: /vue3-project/src/views/layout/menu.vue
-->
<template>
<a-menu :inlineCollapsed='true' theme="dark" mode="inline" v-model:selectedKeys="selectedKeys">
    <a-menu-item key="/home">
        <router-link to="/home">home </router-link>
    </a-menu-item>

    <a-sub-menu key="sub2" @titleClick="titleClick">
        <template v-slot:title>
            <span>
                <AppstoreOutlined /><span>信息</span>
            </span>
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
import {
    toRefs,
    reactive,
    watch,
    watchEffect
} from 'vue'
import {
    useRoute,
    onBeforeRouteUpdate

} from 'vue-router'
export default {
    setup(props) {
        const route = useRoute()
        const state = reactive({
            selectedKeys: [],
        });
        watch(() => route.path, (val, oldval) => {
            console.log(val, 'valvalval')
            state.selectedKeys = [...val]
        });
        return {
            ...toRefs(state)
        }
    },

}
</script>

<style >

</style>
