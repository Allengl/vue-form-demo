<template>
  <div id="app">
    <a-form
        id="components-form-demo-normal-login"
        :form="form"
        class="login-form"
        @submit.prevent="onSubmit"
    >
      <a-form-item>
        <a-input
            v-decorator="[
          'username',
          { rules: [{ required: true, message: '你丫没填用户名！' }] },
        ]"
            placeholder="用户名"
        >
          <a-icon slot="prefix" type="user" style="color: rgba(0,0,0,.25)"/>
        </a-input>
      </a-form-item>
      <a-form-item>
        <a-input
            v-decorator="[
          'password',
          { rules: [{ required: true, message: '你丫没填密码！' },
            {min:8,message:'密码最少8个字符' },
            {pattern: /[a-zA-z]/, message: '必须包含至少一个字母'}
            ]}
        ]"
            type="password"
            placeholder="密码"
        >
          <a-icon slot="prefix" type="lock" style="color: rgba(0,0,0,.25)"/>
        </a-input>
      </a-form-item>
      <a-form-item>
        <a-button type="primary" html-type="submit" class="login-form-button">
          登录
        </a-button>
      </a-form-item>
    </a-form>
  </div>
</template>

<script>
export default {
  beforeCreate() {
    this.form = this.$form.createForm(this, {name: 'normal_login'})
  },
  methods: {
    onSubmit(e) {
      console.log(e)
      this.form.validateFields((error, values) => {
        if (!error) {
          console.log('data:', values)
        } else {
          console.log('error:', error)
        }
      })
    }
  }
}
</script>


