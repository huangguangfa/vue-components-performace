<template>
  <div class="test">
    测试组件AAAA{{ names }}
    <button @click="update">更新AAA</button>
    <div class="datas" v-if="list.length">
      <div v-for="item in list">
        {{ item.name }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: 'zs',
      num: 1,
      list: []
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
          resolve(Array(50000).fill(1).map((_, index) => ({
            name: "test" + index,
          })))
        }, 1000)
      })
      this.list = await p
    }
  },
}
  
</script>