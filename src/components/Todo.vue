<script setup lang="ts">
import { getTodos } from '../services/Api.service';

import { onMounted, ref } from 'vue'
import { ITodo } from '../services/Api.type';

const todos = ref<ITodo[]>([]);

onMounted(async () => {
    console.log(`the component is now mounted.`)
    const data = await getTodos();
    todos.value = data;
})

</script>

<template>
    <p>{{ todos.length }}</p>
    <div v-for="todo of todos">
        <p>{{ todo.title }}</p>
    </div>
</template>