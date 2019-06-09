<template>
    <div>
        <div v-bind:key="todo.id" v-for="todo in todoitems">
            <!-- <h3>{{todo.title}}</h3> -->
            <TodoItem v-bind:todoitem="todo"
            v-on:del-todo="$emit('del-todo', todo.id)"/>
        </div>
    </div>
</template>

<script>
import TodoItem from './TodoItem.vue'

export default {
    name: "Todolist",
    components: {
        TodoItem
    },
    props: ["todoitems"]
}
</script>

