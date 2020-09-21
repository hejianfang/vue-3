<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <p>{{count}}</p>
    <p>{{state.str}}</p>
    <button @click="add">加一</button>
    <button @click="prep">减一</button>
  </div>
</template>

<script>
import { reactive, ref, getCurrentInstance } from 'vue'
export default {
  setup () {
    const state = reactive({
      count: 0,
      str: 'hello'
    })
    const count = ref(0)
    const add = () => {
      count.value++
    }
    const prep = () => {
      if (count.value === 0) return
      count.value--
    }
    const init = () => {
      console.log('加载执行')
    }
    init()
    return {
      state,
      add,
      count,
      prep
    }
  }
}
</script>
