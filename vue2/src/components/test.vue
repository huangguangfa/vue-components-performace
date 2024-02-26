<template>
  <div class="test">
    测试组件A{{ names }}
    <button @click="update">更新</button>
    <div class="datas" v-if="list.length">
      <div v-for="item in list">
        {{ item.name }}
      </div>
    </div>
    <!-- <TestA></TestA> -->
  </div>
</template>

<script>
// import TestA from './testA.vue'
export default {
  components: {
    // TestA
  },
  data() {
    return {
      name: 'zs',
      num: 1,
      list:[]
    }
  },
  created() {
    this.getData()
  },
  computed: {
    names() {
      return this.name + this.num
    }
  },
  methods: {
    async update() {
      await this.getData()
    },
    async getData() {
      const p = new Promise((resolve) => {
        setTimeout(() => {
          resolve(Array(10000).fill(1).map((_, index) => ({
            name: "test" + index,
          })))
        }, 1000)
      })
      this.list = await p
    }
  },
}
  
</script>