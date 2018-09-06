<template>
  <div class="checkbox-detail">
    <el-checkbox-group v-model="checkboxGroup" size="mini">
      <el-checkbox label="备选项1" border></el-checkbox>
      <el-checkbox label="备选项2" border></el-checkbox>
    </el-checkbox-group>
  </div>
</template>

<script>
export default {
  data () {
    return {
      checkboxGroup: []
    }
  }
}
</script>

<style>
.el-checkbox__input{
  display: none;
}
.el-checkbox__label {
  padding-left: 5px;
}
.el-checkbox-group .el-checkbox {
  line-height: 20px;
}
</style>
