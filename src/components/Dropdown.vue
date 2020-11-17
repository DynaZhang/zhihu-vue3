<template>
  <div class="dropdown">
    <a href="#" class="btn btn-outline-light my-2 dropdown-toggle" id="dropdown-toggle" data-toggle="dropdown" aria-expanded="false">{{title}}</a>
  </div>
  <ul class="dropdown-menu" aria-labelledby="dropdown-toggle">
    <li>
      <a href="#" class="dropdown-item">新建文章</a>
    </li>
    <li>
      <a href="#" class="dropdown-item">我的专栏</a>
    </li>
    <li>
      <a href="#" class="dropdown-item">编辑资料</a>
    </li>
    <li>
      <a href="#" class="dropdown-item">退出登录</a>
    </li>
  </ul>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
export default defineComponent({
  name: 'Dropdown',
  props: {
    title: {
      type: String,
      required: true
    }
  }
})
</script>

<style scoped>

</style>
