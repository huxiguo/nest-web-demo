<script setup lang="ts">
import type { FormProps } from 'element-plus'

const labelPosition = ref<FormProps['labelPosition']>('right')

const formLabelAlign = reactive({
  name: '',
  password: '',
  code: ''
})

const codeUrl = ref<string>('/api/validate-code/code')
const onSubmit = () => {
  fetch('/api/validate-code/create', {
    method: 'post',
    body: JSON.stringify(formLabelAlign),
    headers: {
      'content-type': 'application/json'
    }
  })
    .then((res) => res.json())
    .then((res) => console.log(res))
}

const resetCode = () => {
  const time = new Date().getTime()
  codeUrl.value = codeUrl.value + `?${time}`
}
</script>
<template>
  <div>
    <el-form
      :label-position="labelPosition"
      label-width="100px"
      :model="formLabelAlign"
      style="max-width: 460px"
      size="large"
    >
      <el-form-item label="账号">
        <el-input v-model="formLabelAlign.name" />
      </el-form-item>
      <el-form-item label="密码">
        <el-input v-model="formLabelAlign.password" type="password" />
      </el-form-item>
      <el-form-item label="验证码">
        <div style="display: flex">
          <el-input v-model="formLabelAlign.code" />
          <img :src="codeUrl" alt="验证码" @click="resetCode" />
        </div>
      </el-form-item>
      <el-form-item>
        <el-button type="default" @click="onSubmit">登录</el-button>
      </el-form-item>
    </el-form>
  </div>
</template>
