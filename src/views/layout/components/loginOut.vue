<!--
 * @Author: your name
 * @Date: 2020-09-26 15:09:21
 * @LastEditTime: 2020-09-26 15:24:07
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: /vue3-project/src/views/layout/components/loginOut.vue
-->
<template>
<div class="user-info">
    <a-avatar src="https://zos.alipayobjects.com/rmsportal/ODTLcjxAfvqbxHnVXCYX.png" />
    <a-button type="link" @click="loginOut">
        登出
    </a-button>

</div>
</template>

<script>
export default {
    setup(props, context) {
        let loginOut = () => {
            console.log(context)
            alert('登出成功');
        }

        return {
            loginOut
        }
    }
}
</script>

<style lang="less" scoped>
.user-info {
    width: 50vh;
    display: inline-block;
    float: right;
    padding-right: 20px;
    text-align: right;
}
</style>
