# 把父组件的slot传给子组件

```text
Vue.component('W', {
  props: ['child'],
  template: `
  <component :is="child">
    <slot v-for="(_, name) in $slots" :name="name" :slot="name" />
    <template v-for="(_, name) in $scopedSlots" :slot="name" slot-scope="slotData">
      <slot :name="name" v-bind="slotData" />
    </template>
  </component>`
})
```



