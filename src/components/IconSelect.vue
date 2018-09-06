<template>
  <div class="icon-select">
    <el-select v-model="value" placeholder="请选择" popper-class="icon-select" @change="change">
      <el-option
        v-for="item in options"
        :key="item.value"
        :label="item.label"
        :value="item.value"
      >
        <slot :item="item" v-if="value===item.value">
          <!-- 插槽内容 -->
          <i class="el-icon-check"></i>
        </slot>
        <template>
          <span :class="{'icon-select__text': value!==item.value}">{{item.label}}</span>
        </template>
      </el-option>
    </el-select>
  </div>
</template>

<script>
export default {
  props: {
    options: {
      type: Array,
      default: () => []
    }
  },
  data () {
    return {
      value: ''
    }
  },
  methods: {
    change (value) {
      // 选择事件
      this.$emit('selectItem', value)
    }
  }
}
</script>

<style lang="less">
.icon-select {
  display: inline-block;
  .icon-select__text  {
    margin-left: 20px;
  }
  .el-select-dropdown__item {
    padding-left: 5px;
  }
  .el-input__inner {
    padding: 0 25px;
    font-size: 14px;
  }
}
</style>
