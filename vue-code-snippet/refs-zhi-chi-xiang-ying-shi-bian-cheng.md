# refs支持响应式编程

```javascript
import Vue from 'vue'

const ReactiveRefs = function (_Vue) {
  _Vue.mixin({
    beforeCreate() {
      const { refs } = this.$options
      if (!refs) return
      this.$refs = _Vue.observable(
        refs.reduce(($refs, key) => {
          $refs[key] = undefined
          return $refs
        }, {}),
      )
    },
  })
}

Vue.use(ReactiveRefs)

```
