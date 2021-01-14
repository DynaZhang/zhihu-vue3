<template>
  <div class="validate-input-container pb-3">
    <input :type="type" class="form-control" :class="{'is-invalid': inputRef.error}" :value="inputRef.val" @blur="validateInput" @input="handleInput"/>
    <div class="invalid-feedback" v-show="inputRef.error">{{inputRef.message}}</div>
  </div>
</template>

<script lang="ts">
import { defineComponent, PropType, reactive } from 'vue'

interface RuleProp {
  type: 'required' | 'email';
  message: string;
}
export type RulesProp = RuleProp[]

export default defineComponent({
  name: 'ValidateInput',
  props: {
    rules: Array as PropType<RulesProp>,
    modelValue: String,
    type: {
      type: String,
      default: 'text'
    }
  },
  setup (props, context) {
    console.log(props.modelValue)
    const inputRef = reactive({
      val: props.modelValue || '',
      error: false,
      message: ''
    })
    const validateInput = () => {
      const emailReg = /^([a-zA-Z0-9_-])+@([a-zA-Z0-9_-])+(.[a-zA-Z0-9_-])+/
      if (props.rules) {
        const allPassed = props.rules.every(rule => {
          console.log(rule)
          let passed = true
          inputRef.message = rule.message
          switch (rule.type) {
            case 'required': passed = inputRef.val.trim().length > 0; break
            case 'email': passed = emailReg.test(inputRef.val.trim()); break
            default: break
          }
          return passed
        })
        inputRef.error = !allPassed
      }
    }
    const handleInput = (e: KeyboardEvent) => {
      const targetValue = (e.target as HTMLInputElement).value
      inputRef.val = targetValue
      context.emit('update:modelValue', targetValue)
    }
    return {
      validateInput,
      handleInput,
      inputRef
    }
  }
})
</script>

<style scoped>

</style>
