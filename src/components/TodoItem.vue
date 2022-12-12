<template>
  <p :class="['p-todo__item', todoProps.completed ? 'is-completed' : '']">
    <input type="checkbox" :checked="todoProps.completed" v-on:change="markItemCompleted"/>
    {{todoProps.title}}
    <button class="c-btn c-btn--delete" v-on:click="deleteItem">Delete Todo</button>
  </p>
</template>

<script>
// import { ref } from 'vue';
export default {
    name: 'TodoItem',
    props: ['todoProps'],
    setup(props, context) {
        const markItemCompleted = () => {
            context.emit('is-completed', props.todoProps.id)
        }
        const deleteItem = () => {
            context.emit('deleteItem', props.todoProps.id)
        }
        return {
            markItemCompleted,
            deleteItem
        }
    }
}
</script>

<style>

</style>