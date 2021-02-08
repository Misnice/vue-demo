/**
 * 子组件中弹框
 */
<template>
  <div>
    <el-dialog :visible.sync="dialogVisible" title="dialog" width="800">
      <div>内容</div>
      <span slot="footer" class="dialog-footer">
        <el-button @click="dialogVisible = false">取 消</el-button>
        <el-button type="primary" @click="handleConfirm">确 定</el-button>
      </span>
    </el-dialog>
  </div>
</template>

<script>
export default {
  name: 'Sync',
  props: {
    show: {
      type: Boolean,
      default: false
    },
  },
  data() {
    return {
      dialogVisible: false
    }
  },
  watch: {
    show(newVal, oldVal) {
      this.dialogVisible = newVal // show是父组件传过来的值，在子组件不能直接修改，所有弹框的显隐字段要重新声明一个
    },
    dialogVisible(newVal, oldVal) {
      this.$emit('update:show', newVal) // 'update:show' 是专为 .sync修饰符 提供的， show为父组件中.sync绑定的字段
    }
  },
  methods: {
    handleConfirm() {
      this.dialogVisible = false
    }
  }
}
</script>
