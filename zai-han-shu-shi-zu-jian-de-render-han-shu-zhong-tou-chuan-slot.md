# 在函数式组件的render函数中透传slot

## 定义

{% tabs %}
{% tab title="CmponentProvider.vue" %}
```javascript
import { getComponent } from "./component-types"

export default {
  name: "component-provider",
  functional: true,
  render(createElement, context) {
    let slots = context.slots()

    let instance = createElement(getComponent("childComponent"), {
      props: {
        ...context.data.attrs
      }
    }, [
      createElement('template', {slot: "slot-of-child"}, slots['slot-of-partent'])
    ])

    return instance;
  }
}
```

PS:  核心在于下面这行代码，即slot需要手动的传入，可以指定把 `slot-of-parent` 传给  `slot-of-child` ,这里是会为了demo，选用了不同的名字。

```javascript
 createElement('template', {slot: "slot-of-child"}, slots['slot-of-partent'])
    ])
```
{% endtab %}

{% tab title="component-types.js" %}
```javascript
import ChildComponent from "./ChildComponent.vue"

const COMPONENT_MAP = {
  childComponent: ChildComponent,
}

export function getComponent(type) {
  return COMPONENT_MAP[type]
}

```
{% endtab %}

{% tab title="ChildComponent.vue" %}
```jsx
<template>
 <slot name="slot-of-child"></slot>
</template>
<script>
export default {
}
</script>
```
{% endtab %}
{% endtabs %}

## 使用

```jsx
<template>   
   <component-provider>
    <template slot="slot-of-parent">
      slot
    </template>
  </component-provider>
</template>
<script>
import ComponentProvider from './ComponentProvider'
export default {
  components: {
    ComponentProvider
  },
}
</script>
```

