<template>
    <div class="todo-item" v-bind:class="{'is-complete' : todo.completed}"> 
        <p>
            <input type="checkbox" v-on:change="toggleComplete">
            {{todo.title}}
            <button v-on:click="$emit('del-todo', todo.id)" class="del">X</button>
        </p>
    </div>
</template>

<script>
export default {
    name: "TodoItem",
    props: ["todo"],
    methods: {
        toggleComplete() {
            this.todo.completed = !this.todo.completed
        }
    }
}
</script>

<style scoped>
    .todo-item {

    }

    .is-complete {
        text-decoration: line-through;
    }

    .delete {
        color: red;
    }
</style>


