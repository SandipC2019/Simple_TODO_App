<template>
    <div class="todoitem" v-bind:class="{'is-completed' : todoitem.completed}">
        <!-- <p>
            <input type="checkbox" v-on:change="setDone">
            {{todoitem.title}}
            <button @click="$emit('del-todo', todoitem.id)"
                 class="btn btn-danger">
                Delete
            </button>
        </p> -->
        <div class="row" style="padding: 5px;">
            <div class="col-md-10">
                <input type="checkbox" v-on:change="setDone"
                 v-bind:checked="todoitem.completed">
                {{todoitem.title}}
            </div>
            <div class="col-md-2" style="text-align: right;">
                <button @click="$emit('del-todo', todoitem.id)"
                    class="btn btn-danger">
                    Delete
                </button>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "TodoItem",
    props: ["todoitem"],
    methods: {
        setDone() {
            this.todoitem.completed = !this.todoitem.completed;
        }
    }
}
</script>

<style scoped>
    .todoitem {
        background: #666666;
        color: #eeeeee;
        font-weight: bold;
        padding: 3px 3px 3px 3px;
        border-bottom: 1px #bbbbbb solid; 
    }
    .is-completed {
        background: #222222;
        text-decoration: line-through;
    }
</style>


