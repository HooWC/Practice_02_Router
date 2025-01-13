<script setup>
    import { ref } from 'vue';
    import TodoItem from './TodoItem.vue';

    const newTodo = ref('');
    const todos = ref([]);

    const addTodo = () => {
        if(newTodo.value.trim()){
            todos.value.push(newTodo.value.trim());
            newTodo.value = '';
        }
    }

    const deleteTodo = (index) => {
        todos.value.splice(index, 1);
    }
</script>

<template>
    <div>

        <router-link to="/">Home Page</router-link>

        <input v-model="newTodo" @keyup.enter="addTodo" placeholder="Add a new Task" />

        <ul>
            <TodoItem v-for="(todo, index) in todos" :todo="todo" :key="index" @d="deleteTodo(index)" />
        </ul>

    </div>
</template>

<style scoped>
input {
    width: 100%;
    padding: 10px;
    margin-bottom: 10px;
    box-sizing: border-box;
}

ul {
    list-style: none;
    padding: 0;
}
</style>