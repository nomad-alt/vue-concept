<template>
    <div>
        <p>Message from parent: {{ parentMessage }}</p>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import type { PropType } from 'vue';

// Props: Passing data to child components using props.

export default defineComponent({
    name: 'ChildComponent',
    props: {
        parentMessage: {
            type: String as PropType<string>,
            required: true
        }
    }
});
</script>

<style scoped>
p {
    color: #35495e;
}
</style>
