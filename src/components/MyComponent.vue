<template>
    <div>
        <!-- Interpolations -->
        <h1>{{ message }}</h1>
        <p>Computed reversed message: {{ reversedMessage }}</p>

        <!-- HTML Interpolation -->
        <div v-html="rawHtml"></div>

        <!-- Directives -->
        <img :src="imageSrc" alt="Vue logo">

        <!-- v-bind shorthand -->
        <img :src="imageSrc" alt="Vue logo">

        <!-- v-model -->
        <input v-model="inputValue" placeholder="Edit me">
        <p>Input value is: {{ inputValue }}</p>

        <!-- Conditional Rendering -->
        <p v-if="seen">Now you see me</p>
        <p v-else>Now you don't</p>

        <!-- List Rendering -->
        <ul>
            <li v-for="item in items" :key="item.id">{{ item.text }}</li>
        </ul>

        <!-- Event Handling -->
        <button @click="increment">Click me!</button>
        <p>Button clicked {{ count }} times</p>

        <!-- Event Handling with Modifiers -->
        <form @submit.prevent="onSubmit">
            <input type="text" v-model="formInput">
            <button type="submit">Submit</button>
        </form>

        <!-- Attribute Binding -->
        <button :disabled="isDisabled">Disabled Button</button>

        <!-- Class and Style Bindings -->
        <div :class="{ active: isActive }">Class Binding</div>
        <div :style="{ color: activeColor, fontSize: fontSize + 'px' }">Style Binding</div>

        <!-- Props -->
        <ChildComponent :parentMessage="message" />
    </div>
</template>

<script lang="ts">
import { defineComponent, ref, computed, onMounted } from 'vue';
import ChildComponent from './ChildComponent.vue';

export default defineComponent({
    name: 'MyComponent',
    components: {
        ChildComponent
    },
    setup() {
        // Reactivity Fundamentals
        const message = ref('Hello, Vue 3 with TypeScript!');
        const count = ref(0);
        const inputValue = ref('');
        const formInput = ref('');
        const seen = ref(true);
        const isDisabled = ref(true);
        const isActive = ref(true);
        const activeColor = ref('red');
        const fontSize = ref(14);
        const imageSrc = ref('https://vuejs.org/images/logo.png');
        const rawHtml = ref('<span style="color: red;">This is red!</span>');

        // List Rendering
        const items = ref([
            { id: 1, text: 'Learn JavaScript' },
            { id: 2, text: 'Learn Vue' },
            { id: 3, text: 'Build something awesome' }
        ]);

        // Computed Properties
        const reversedMessage = computed(() => message.value.split('').reverse().join(''));

        // Event Handling
        const increment = () => {
            count.value++;
        };

        // Form Submit Handler
        const onSubmit = () => {
            console.log('Form submitted with', formInput.value);
        };

        // Lifecycle Hooks (Mounted)
        onMounted(() => {
            console.log('MyComponent is mounted!');
        });

        return {
            message,
            count,
            inputValue,
            formInput,
            seen,
            isDisabled,
            isActive,
            activeColor,
            fontSize,
            imageSrc,
            rawHtml,
            items,
            reversedMessage,
            increment,
            onSubmit
        };
    }
});
</script>

<style scoped>
h1 {
    color: #42b983;
}

.active {
    font-weight: bold;
}
</style>
