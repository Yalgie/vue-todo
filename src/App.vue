<template>
    <div id="app">
        <Header />
        <img alt="Vue logo" src="./assets/logo.png">
        <AddTodo v-on:add-todo="addTodo" />
        <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" />
    </div>
</template>

<script>
import axios from 'axios';

import Header from './components/layout/Header.vue';

import Todos from './components/Todos.vue';
import AddTodo from './components/AddTodo.vue';

export default {
    name: 'app',
    components: {
        Todos,
        Header,
        AddTodo
    },
    data() {
        return {
            todos: []
        }
    },
    methods: {
        deleteTodo(id) {
            this.todos = this.todos.filter(todo => todo.id !== id);
        },
        addTodo(newTodo) {
            this.todos = [...this.todos, newTodo];
        }
    },
    created() {
        axios.get("https://jsonplaceholder.typicode.com/todos?_limit=5").then((res) => {
            this.todos = res.data;
        }).catch((e) => {
            throw e;
        });
    }
}
</script>

<style>
#app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
}
</style>
