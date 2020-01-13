# 把父组件的slot传给子组件

```javascript
<slot v-for="(_, name) in $slots" :name="name" :slot="name" />
<template v-for="(_, name) in $scopedSlots" :slot="name" slot-scope="slotData">
  <slot :name="name" v-bind="slotData" />
</template>
```

原文地址： [Vue: Pass Slots through from Parent to Child Components](https://gist.github.com/Loilo/73c55ed04917ecf5d682ec70a2a1b8e2)

