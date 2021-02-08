<template>
  <div class="content">
    <el-button type="primary" @click="dialogVisible = true">父组件按钮</el-button>
    <Sync :show.sync="dialogVisible" />
  </div>
</template>

<script>
// vue中.sync修饰符实现父组件与子组件的双向数据绑定
import Sync from '@/components/Sync.vue'

export default {
  name: 'TwoWayData',
  components: {
    Sync
  },
  data() {
    return {
      dialogVisible: false
    }
  },
  watch: {
    dialogVisible(newVal, oldVal) {
      console.log('父组件值', newVal, oldVal)
    }
  },
  mounted() { }
}
</script>

<style scoped lang="scss">
.content {
  padding: 20px 0;
}
</style>
