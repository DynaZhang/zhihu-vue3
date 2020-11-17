<template>
  <global-header :user="user" />
  <column-list :list="columnList"/>
</template>

<script lang="ts">
import ColumnList from './components/ColumnList.vue'
import GlobalHeader from './components/GlobalHeader.vue'
import { defineComponent, ref, onMounted } from 'vue'

interface ColumnProp {
  id: number;
  title: string;
  avatar: string;
  description: string;
}

export default defineComponent({
  name: 'App',
  components: {
    ColumnList,
    GlobalHeader
  },
  setup () {
    const columnList = ref([] as ColumnProp[])
    const user = ref({ isLogin: false })
    onMounted(() => {
      columnList.value = [
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
    })
    return {
      columnList,
      user
    }
  }
})
</script>

<style>

</style>
