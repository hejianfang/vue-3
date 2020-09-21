<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <p>{{state.count}}</p>
    <p>{{state.str}}</p>
    <p>{{state.double}}</p>
    <button @click="add">加一</button>
    <button @click="prep">减一</button>
  </div>
</template>

<script>
import { reactive, computed, watch, getCurrentInstance } from 'vue'
export default {
  setup () {
    const { ctx } = getCurrentInstance()
    const store = ctx.$store
    console.log(store.state)
    const state = reactive({
      count: 100,
      str: 'hello',
      double: computed(() => state.count * 2)
    })
    watch(() => state.count, val => {
      console.log(`count is ${val}`)
    })
    const add = () => {
      state.count++
    }
    const prep = () => {
      if (state.count === 0) return
      state.count--
    }
    return {
      state,
      add,
      prep
    }
  }
}
</script>
