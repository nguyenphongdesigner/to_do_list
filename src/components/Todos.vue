<template>
    <div class="p-todo mt-50">
        <TodoItem 
        v-for="todoItem in todoList" 
        v-bind:key="todoItem.id" 
        v-bind:todoProps="todoItem" 
        v-on:is-completed = "markCompleted"
        v-on:deleteItem = "deleteTodo"
        class="p-todo__item" />
    </div>
</template>

<script>
import {ref} from  'vue';
import TodoItem from './TodoItem.vue'
export default {
    name: 'Todos',
    components: {TodoItem},
    setup() {
        const todoList = ref([
            {
                id: 1,
                title: 'Cong Viec 1',
                completed: false
            },
            {
                id: 2,
                title: 'Cong Viec 2',
                completed: false
            },
            {
                id: 3,
                title: 'Cong Viec 3',
                completed: false
            }
        ])
        const markCompleted = id =>{
            todoList.value = todoList.value.map(todoList => {
                if(todoList.id === id) todoList.completed = !todoList.completed
                return todoList
            })
        }
        const deleteTodo = id => {
            todoList.value = todoList.value.filter(todoList => todoList.id !== id)
        }
        return {
            todoList,
            markCompleted,
            deleteTodo
        }
    }
}
</script>

<style>
    @import "../assets/styles/object/project/_todos.scss";
</style>