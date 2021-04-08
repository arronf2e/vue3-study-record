<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <HelloWorld :msg="msg" />
  <Render />
  <button @click="changemsg">change msg</button>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue'
import HelloWorld from './components/HelloWorld.vue'
import Render from './components/render.vue'

export default defineComponent({
  name: 'App',
  components: {
    HelloWorld,
    Render
  },
  setup() {
    const msg = ref('Hello Vue 3 + TypeScript + Vite')

    const changemsg = () => msg.value = 'good change'

    return {
      msg,
      changemsg
    }
  }
})
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>