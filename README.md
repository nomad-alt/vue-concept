# vue-concept

## Concepts Demonstrated

Reactivity Fundamentals
In Vue 3, reactivity is achieved using the ref and reactive functions. In this project, we use ref to create reactive references that store primitive values.

### Reactivity Fundamentals

In Vue 3, reactivity is achieved using the ref and reactive functions. In this project, we use ref to create reactive references that store primitive values.

```
import { ref } from 'vue';

const message = ref('Hello, Vue 3 with TypeScript!');
const count = ref(0);
```

### Computed Properties

Computed properties are used to create reactive derived state. They are defined using the computed function.

```
import { computed } from 'vue';

const reversedMessage = computed(() => message.value.split('').reverse().join(''));
```

### Event Handling

Event handling in Vue is done using the v-on directive or its shorthand @. This allows you to listen to DOM events and execute methods.

```
<button @click="increment">Click me!</button>

const increment = () => {
  count.value++;
};
```

### Template Syntax

Vue's template syntax allows you to declaratively bind data to the DOM using special directives and expressions.

Text Interpolation: {{ message }}
HTML Interpolation: <div v-html="rawHtml"></div>
Attribute Binding: <img :src="imageSrc" alt="Vue logo">
Class and Style Bindings:

```
<div :class="{ active: isActive }">Class Binding</div>
<div :style="{ color: activeColor, fontSize: fontSize + 'px' }">Style Binding</div>
```

Conditional Rendering:

```
<p v-if="seen">Now you see me</p>
<p v-else>Now you don't</p>
```

List Rendering:

```
<ul>
  <li v-for="item in items" :key="item.id">{{ item.text }}</li>
</ul>
```

### Props

Props are custom attributes passed from a parent component to a child component. They allow data to flow from parent to child.

Parent Component (MyComponent.vue)

```
<ChildComponent :parentMessage="message" />
```

Child Component (ChildComponent.vue)

```
props: {
  parentMessage: {
    type: String as PropType<string>,
    required: true
  }
}
```

###Lifecycle Hooks (Mounted)
Lifecycle hooks are functions that are called at specific stages of a component's lifecycle. The onMounted hook is called after the component is mounted to the DOM.

```
import { onMounted } from 'vue';

onMounted(() => {
  console.log('MyComponent is mounted!');
});
```
