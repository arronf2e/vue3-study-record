<template>
  <h1>{{ msg }}</h1>
  <h1>{{ obj.name }}</h1>
  <h1>{{ count }}</h1>
  <button @click="countAdd">count++</button>
</template>

<script lang="ts">
import { ref, defineComponent, onMounted, reactive, onRenderTracked, onRenderTriggered, onErrorCaptured, onUpdated, onBeforeUpdate, onBeforeUnmount, onUnmounted, onActivated, onDeactivated, watchEffect, toRefs } from 'vue'
export default defineComponent({
  name: 'HelloWorld',
  props: {
    msg: {
      type: String,
      required: true
    }
  },

  mounted() {
    console.log('also mounted');
  },

  beforeCreate() {
    console.log('hello before create');
  },

  created() {
    console.log('hello created');
  },

  setup: (props, ctx) => {
    watchEffect(() => {
      console.log(props.msg, 'props.msg');
    })

    const { msg } = toRefs(props)

    console.log(ctx.attrs, ctx.slots, ctx.emit, 'ctx', msg);
    const countAdd = () => count.value++

    onMounted(() => {
      console.log('hello mounted');
    })

    onBeforeUpdate((e: any) => {
      console.log(e, 'before update');
    })

    onUpdated(() => {
      console.log('updated');
    })

    onBeforeUnmount(() => {

    })
    
    onUnmounted(() => {

    })

    onActivated(() => {
      console.log('onActivated');
      
    })

    onRenderTracked((event) => {
      // console.log('hello onrendertracked', event);
    })

    onRenderTriggered((event) => {
      console.log('hello onRenderTriggered', event);
    })

    onErrorCaptured((event) => {
      console.log(event, 'event');
    })

    const count = ref(0)
    const obj = reactive({
      name: 'obj2'
    })
    return { count, obj, countAdd }
  }
})
</script>

<style scoped>
a {
  color: #42b983;
}

label {
  margin: 0 0.5em;
  font-weight: bold;
}

code {
  background-color: #eee;
  padding: 2px 4px;
  border-radius: 4px;
  color: #304455;
}
</style>
