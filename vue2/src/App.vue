<script>
import Test from './components/test.vue'
export default {
  components: {
    Test
  },
  data() {
    return {
      name: '张三',
      show: false
    }
  },
  methods: {
    showComponent() {
      this.show = true
    }
  }
}
</script>

<template>
  <div id="app">
    {{ name }}
    <button @click="showComponent">显示组件</button>
    <Test v-if="show"></Test>
  </div>
</template>

