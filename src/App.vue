<template>
    <div id="app">
        <img alt="Vue logo" src="./assets/neds-logo.png">
        <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" />
    </div>
</template>

<script>
import Todos from './components/Todos.vue'

export default {
    name: 'app',
    components: {
        Todos
    },
    data() {
        return {
            todos: [{
                id: 1,
                title: "Title 1",
                completed: false
            }, {
                id: 2,
                title: "Title 2",
                completed: false
            }, {
                id: 3,
                title: "Title 3",
                completed: false
            }]
        }
    },
    methods: {
        deleteTodo(id) {
            this.todos = this.todos.filter(todo => todo.id !== id);
        }
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
