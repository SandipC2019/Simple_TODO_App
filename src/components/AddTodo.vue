<template>
    <div class="addTodo">
        <form @submit="addTodo">
            <div class="row">
                <div class="col-md-10">
                    <input type="text" v-model="title" name="title"
                    placeholder="Enter Todo Title" class="form-control" >
                </div>
                <div class="col-md-2" style="text-align: right;">
                    <input type="submit" value="  Add  " class="btn btn-success">
                </div>
            </div>
        </form>
    </div>
</template>

<script>
//import uuid from 'uuid';

export default {
    name: "AddTodo",
    data() {
        return {
            title: ''
        }
    },
    methods: {
        addTodo(e) {
            e.preventDefault();
            const newTodoItem = {
                //id: uuid.v4(),
                title: this.title,
                completed: false
            };

            this.$emit('add-todo', newTodoItem);
            this.title = null;
        }
    }
}
</script>

<style scoped>
    .addTodo {
        background: #36daf7;
        padding: 8px;
    }
</style>


