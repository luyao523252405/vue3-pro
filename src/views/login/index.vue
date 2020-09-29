<!--
 * @Author: your name
 * @Date: 2020-09-29 15:43:41
 * @LastEditTime: 2020-09-29 20:08:27
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: /vue3-project/src/views/login/index.vue
-->
<template>
  <div class="login-box" v-if="!isLogin">
    <div class="login">
      <h3>登陆页面</h3>
      <a-form @submit="handleSubmit">
        <a-form-item>
          <a-input v-model:value="form.user" placeholder="请输入用户账号">
          </a-input>
        </a-form-item>
        <a-form-item>
          <a-input
            v-model:value="form.password"
            type="password"
            placeholder="请输入登陆密码"
          >
          </a-input>
        </a-form-item>
        <a-form-item>
          <a-button
            type="primary"
            html-type="submit"
            :disabled="form.user === '' || form.password === ''"
          >
            登陆
          </a-button>
        </a-form-item>
      </a-form>
    </div>
  </div>
</template>

<script>
import { reactive, toRefs } from "vue";
import { useRouter } from "vue-router";
export default {
  setup() {
    let router = useRouter();
    let state = reactive({
      form: {
        user: "",
        password: "",
      },
      isLogin: localStorage.getItem("login"),
    });

    if (state.isLogin) {
      router.push({ name: "layout" });
    } else {
      state.isLogin = false;
      localStorage.setItem("login", false);
    }

    const handleSubmit = (e) => {
      localStorage.setItem("login", true);
      router.go(0);
    };

    return {
      ...toRefs(state),
      handleSubmit,
    };
  },
};
</script>

<style lang="less" scoped>
.login-box {
  background-color: #509e7c;
}
.login {
  text-align: center;
  background-color: white;
  width: 400px;
  padding: 50px;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate3d(-50%, -50%, 0);
}
</style>