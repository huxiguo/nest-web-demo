<script setup lang="ts">
import type { FormProps } from 'element-plus'

const labelPosition = ref<FormProps['labelPosition']>('right')

const formLabelAlign = reactive({
  name: '',
  region: '',
  type: ''
})

const onSubmit = () => {
  console.log(123)
}
</script>
<template>
  <div>
    <el-form
      :label-position="labelPosition"
      label-width="100px"
      :model="formLabelAlign"
      style="max-width: 460px"
      size="large s"
    >
      <el-form-item label="账号">
        <el-input v-model="formLabelAlign.name" />
      </el-form-item>
      <el-form-item label="密码">
        <el-input v-model="formLabelAlign.region" />
      </el-form-item>
      <el-form-item label="验证码">
        <el-input v-model="formLabelAlign.type" />
      </el-form-item>
      <el-form-item>
        <el-button type="default" @click="onSubmit">登录</el-button>
      </el-form-item>
    </el-form>
  </div>
</template>
