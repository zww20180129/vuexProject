<template>
  <div class="login">
    <h1>普通登录组件</h1>
    <div class="account">
      <account-login
        :rule-form="ruleForm"
        :rules="rules"
        @submit="submit"
        @errHandle="errHandle"
      ></account-login>
    </div>
    <h1>短信验证码登录组件</h1>
    <div class="phone">
      <phone-login
        :rule-form="phoneForm"
        @send="send"
        @submit="submit"
        @errHandle="errHandle"
      ></phone-login>
    </div>
  </div>
</template>
<script>
export default {
  name: 'Login',
  data() {
    return {
      ruleForm: {
        username: '',
        password: '',
      },
      phoneForm: {
        phone: '',
        code: '',
      },
      rules: {
        username: [
          {
            required: true,
            message: '用户名不能为空',
            trigger: 'blur',
          },
          {
            min: 2,
            max: 6,
            message: '用户名在2到6个字符之间',
            trigger: 'blur',
          },
        ],
        password: [
          {
            required: true,
            message: '密码不能为空',
            trigger: 'blur',
          },
          {
            min: 2,
            max: 6,
            message: '密码在6到15个字符之间',
            trigger: 'blur',
          },
        ],
      },
    }
  },
  methods: {
    submit() {
      this.$message.success('提交成功')
    },
    errHandle() {
      this.$message.error('表单填写有误')
    },
    send() {
      //这里可以写发送验证码成功后的逻辑
      this.$message.info('发送验证码成功')
    },
  },
}
</script>
<style  scoped>
.login {
  margin: 30px;
  margin-left: 30px;
}
.account,
.phone {
  width: 500px;
}
</style>