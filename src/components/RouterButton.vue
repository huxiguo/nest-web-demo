<script setup lang="ts">
const router = useRouter()

interface Props {
  type?: string
  text?: string
  toPath?: string
}
const props = withDefaults(defineProps<Props>(), {
  type: 'success',
  text: '主页',
  toPath: '/'
})
const handleToPath = (path: string) => {
  router.push(path)
}
</script>
<template>
  <el-button :type="props.type" @click="handleToPath(props.toPath)">{{ props.text }}</el-button>
</template>
