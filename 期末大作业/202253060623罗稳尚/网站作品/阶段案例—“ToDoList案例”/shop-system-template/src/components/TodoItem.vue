<template>
    <li :class="{completd:todo?.completed}">
        {{ todo?.title }}
        <button @click="toggleTodo">任务已经完成</button>
        <button @click="deteleTodo">删除</button>
    </li>
</template>

<script lang="ts" setup>
import { emptyProps } from 'vant';
import { defineProps } from 'vue';

interface Todo {
    id:Number;
    title: String;
    completed:Boolean;
}

const props =defineProps ({
    todo:Object as ()=> Todo
})

const emit = defineEmits(['toggle-todo', 'detele-todo'])

const toggleTodo=()=>{
    console.log("任务已完成通用方法")
    emit ('toggle-todo',props.todo?.id)
}

const deteleTodo=()=>{
    console.log("对当前任务进行删除")
    emit ('detele-todo',props.todo?.id)
}

</script>
<style>
li {
    display: flex;
    justify-content: space-between;
    align-items: center;
}
button {
    padding: 5px 10px;
    background-color: #d9534f;
    border: none;
    border-radius: 4px;
    color: white;
    cursor: pointer;
}
button:hover {
    background-color: #c9302c;
}
.completed {
    color: #777;
    text-decoration: line-through;
}
</style>