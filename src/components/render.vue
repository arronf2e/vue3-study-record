<script>
import { defineComponent, h, ref, reactive } from 'vue'
export default defineComponent({
  setup() {
    const year = ref(2021)
    const me = reactive({
      name: 'arron',
      age: 28
    })
    return () => h('div', [year.value, me.name])
  },
})
</script>
