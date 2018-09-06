<template>
  <div class="number-input">
    <el-form :model="ruleForm2" :rules="rules2" ref="ruleForm2" label-width="100px" class="demo-ruleForm">
      <el-form-item :label="label" prop="age">
        <el-input v-model="ruleForm2.age"></el-input>
      </el-form-item>
    </el-form>
  </div>
</template>

<script>
export default {
  props: {
    // 允许输入的最大值
    maxValue: {
      type: Number,
      default: 99999
    },
    // 小数点位数
    fixedValue: {
      type: Number,
      default: 2
    },
    // 是否是必填
    requireValue: {
      type: Boolean,
      default: true
    },
    // 允许输入的最小值
    minValue: {
      type: Number,
      default: 0
    },
    // 表单的说明
    label: {
      type: String,
      default: '金额'
    }
  },
  data () {
    var checkAge = (rule, value, callback) => {
      if (value.trim() === '') {
        if (this.requireValue) {
          callback(new Error('值不能为空'))
        } else {
          callback()
        }
      }
      if (isNaN(value)) {
        callback(new Error('请输入数字'))
      }
      if (value < this.minValue) {
        callback(new Error(`最小值${this.minValue}`))
      }
      if (!this.fixedValue) {
        let len = (this.maxValue + '').length - 1
        let reg = new RegExp(`^(\\d|[1-9]\\d{1,${len}})$`)
        if (reg.test(value)) {
          callback()
        } else {
          callback(new Error(`请输入${this.minValue}-${this.maxValue}的整数`))
        }
      } else {
        let len = (this.maxValue + '').length - 1
        let reg = new RegExp(`^(\\d|[1-9]\\d{1,${len}})(\\.\\d{1,${this.fixedValue}})?$`)
        if (reg.test(value)) {
          callback()
        } else {
          callback(new Error(`请输入${this.minValue}-${this.maxValue}的整数或小数（支持小数点后${this.fixedValue}位）`))
        }
      }
    }

    return {
      ruleForm2: {
        age: ''
      },
      rules2: {
        age: [
          { validator: checkAge, trigger: ['blur', 'change'], required: this.requireValue }
        ]
      }
    }
  },
  methods: {
    submitForm (formName) {
      this.$refs[formName].validate((valid) => {
        if (valid) {
          alert('submit!')
        } else {
          console.log('error submit!!')
          return false
        }
      })
    },
    resetForm (formName) {
      this.$refs[formName].resetFields()
    }
  }
}
</script>

<style scoped>
.number-input {
  display: inline-block;
  width: 400px;
}
</style>
