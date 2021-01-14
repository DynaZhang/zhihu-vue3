<template>
  <div class="container">
    <global-header :user="user" />
    <form>
      <div class="mb-3">
        <div class="form-label">Email address</div>
        <validate-input v-model="email" :rules="emailRules" />
      </div>
      <div class="mb-3">
        <label for="exampleInputPassword1" class="form-label">Password</label>
        <input type="password" class="form-control" id="exampleInputPassword1">
      </div>
      <div class="mb-3 form-check">
        <input type="checkbox" class="form-check-input" id="exampleCheck1">
        <label class="form-check-label" for="exampleCheck1">Check me out</label>
      </div>
      <button type="button" class="btn btn-primary">Submit</button>
    </form>
<!--    <column-list :list="testData"/>-->
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive, toRefs, ref } from 'vue'
import ValidateInput, { RulesProp } from './components/ValidateInput.vue'
import { ColumnProp } from './components/ColumnList.vue'
import GlobalHeader, { UserProp } from './components/GlobalHeader.vue'

export default defineComponent({
  name: 'App',
  components: {
    GlobalHeader, ValidateInput
  },
  setup () {
    const email = ref('12312312')
    const emailRules: RulesProp = reactive([
      { type: 'required', message: '请输入邮箱' },
      { type: 'email', message: '请输入正确的邮箱格式' }
    ])
    const testData: ColumnProp[] = [
      {
        id: 1,
        title: 'test1的专栏',
        description: '这是的test1专栏，有一段非常有意思的简介，可以更新一下欧',
        avatar: 'http://vue-maker.oss-cn-hangzhou.aliyuncs.com/vue-marker/5ee22dd58b3c4520912b9470.jpg?x-oss-process=image/resize,m_pad,h_100,w_100'
      },
      {
        id: 2,
        title: 'test2的专栏',
        description: '这是的test2专栏，有一段非常有意思的简介，可以更新一下欧',
        avatar: 'http://vue-maker.oss-cn-hangzhou.aliyuncs.com/vue-marker/5ee22dd58b3c4520912b9470.jpg?x-oss-process=image/resize,m_pad,h_100,w_100'
      }
    ]
    const user: UserProp = {
      isLogin: true,
      name: '江户川',
      id: 1
    }
    const data = reactive({
      testData,
      user,
      emailRules
    })
    const refData = toRefs(data)
    return {
      ...refData,
      email
    }
  }
})
</script>

<style>

</style>
