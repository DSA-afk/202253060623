<template>
    <h1>任务列表</h1>
    <ul>
        <!--任务列表组件页面-->
        <TodoItem v-for=" todo in list" :todo="todo" :key="todo.id"  @toggle-todo="toggleTodo" @detele-todo="deteleTodo"></TodoItem>
    </ul>
</template>

<script lang="ts" setup>
import { defineProps } from 'vue';
import TodoItem from './TodoItem.vue';

interface Todo {
    id:Number;
    title: String;
    completed:Boolean;
}

const props = defineProps({
    list:Array as ()=>Todo[]
})

const emit= defineEmits(['toggle-todo','detele-todo'])

//任务完成
const toggleTodo=(id:number)=> {
    console.log(id)
    emit('toggle-todo',id)
}

//删除
const deteleTodo=(id:number)=> {
    console.log(id)
    emit('detele-todo',id)
}

</script>
<style scoped>
ul {
    list-style: none;
    padding: 0;
}
li {
    padding: 10px;
    border-bottom: 1px solid #ddd;
}
li:last-child {
    border-bottom: none;
}
</style>