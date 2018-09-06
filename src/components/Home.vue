<template>
  <div>
    <h1>带图标选中的下拉</h1>
    <icon-select :options="options">
    </icon-select>
    <h1>带图标的下拉选择</h1>
    <list-select :options="options" @selectItem="selectItem">
      <template slot-scope="options">
          <i :class="options.item.icon"></i>
          <span style="margin-left:4px;">{{options.item.label}}</span>
      </template>
      <i slot="prefix" class="el-input__icon el-icon-search"></i>
    </list-select>
  </div>
</template>

<script>
import NumberInput from './NumberInput'
import IconSelect from './IconSelect'
import ListSelect from './ListSelect'

export default {
  components: {
    NumberInput,
    IconSelect,
    ListSelect
  },
  data () {
    return {
      options: [{
        value: '选项1',
        label: '黄金糕',
        icon: 'el-icon-time'
      }, {
        value: '选项2',
        label: '双皮奶',
        icon: 'el-icon-bell'
      }, {
        value: '选项3',
        label: '蚵仔煎',
        icon: 'el-icon-mobile-phone'
      }, {
        value: '选项4',
        label: '龙须面',
        icon: 'el-icon-service'
      }],
      value: ''
    }
  },
  methods: {
    selectItem (value) {
    }
  }
}
</script>
