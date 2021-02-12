<script>
import { h, ref, watchEffect } from 'vue'

import Another from './Another.vue'

export default {
  props: {
    msg: String,
  },
  setup(props) {
    const element = ref()
    watchEffect(() => {
      console.log(element.value, '...')
    })
    return () => {
      return h(Another, {ref: element, msg: props.msg})
      // same:
      //return h(Another, {ref: (el) => element.value = el, msg: props.msg})
    }
  }
}
</script>
