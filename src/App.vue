<template>
  <div class="container">
    <global-header :user="user" />
    <column-list :list="testData"/>
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive, toRefs } from 'vue'
import ColumnList, { ColumnProp } from './components/ColumnList.vue'
import GlobalHeader, { UserProp } from './components/GlobalHeader.vue'

export default defineComponent({
  name: 'App',
  components: {
    ColumnList, GlobalHeader
  },
  setup () {
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
      user
    })
    const refData = toRefs(data)
    return {
      ...refData
    }
  }
})
</script>

<style>

</style>
