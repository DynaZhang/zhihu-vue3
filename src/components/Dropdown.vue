<template>
  <div class="dropdown" ref="dropdownRef">
    <a href="#" class="btn btn-outline-light my-2 dropdown-toggle" @click.prevent="toggleOpen">
      {{title}}
    </a>
    <ul class="dropdown-menu" :style="{display: 'block'}" v-if="isOpen && !isClickOutside">
      <slot />
    </ul>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue'
import useClickOutside from '../hooks/useClickOutside'

export default defineComponent({
  name: 'Dropdown',
  props: {
    title: {
      type: String,
      required: true
    }
  },
  setup () {
    const isOpen = ref(false)
    const toggleOpen = () => {
      isOpen.value = !isOpen.value
    }
    const dropdownRef = ref<HTMLElement | null>(null)
    const isClickOutside = useClickOutside(dropdownRef)

    return {
      isOpen,
      toggleOpen,
      dropdownRef,
      isClickOutside
    }
  }
})
</script>

<style scoped>

</style>
