<template>
<div class="list-select">
  <el-select v-model="value" placeholder="请选择" popper-class="list-select" @change="change">
    <el-option
      v-for="item in options"
      :key="item.value"
      :label="item.label"
      :value="item.value"
    >
      <slot :item="item">
        <!-- 插槽内容 -->
        <span class="list-select__text">{{item.label}}</span>
      </slot>
    </el-option>
  </el-select>
  <div class="list-select__input" v-if="value">
    <slot name="prefix">
    </slot>
  </div>
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
.list-select {
  position: relative;
  text-align: left;
  display: inline-block;
  &__input {
    position: absolute;
    left: 0;
    top: 0;
  }
  .el-input__inner {
    padding: 0 25px;
    font-size: 14px;
  }
}
.list-select {
  .list-select__text {
    margin-left: 20px;
  }
  .el-select-dropdown__item {
    padding-left: 5px;
  }
}
</style>
