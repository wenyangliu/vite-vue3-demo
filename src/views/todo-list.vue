<template>
  <div class="todo-list">
    <div>
      <label>新增代办</label>
      <input v-model="state.todo" @keyup.enter="handleAddTodo">
    </div>
    <div>
      <h3>代办列表{{todos.length}}</h3>
      <ul>
        <li v-for="item in todos" :key="item.id" @click="handleChangeStatus(item, true)">
          <input type="checkbox">
          <label>{{item.text}}</label>
        </li>
      </ul>
    </div>
    <div>
      <h3>已办列表{{dones.length}}</h3>
      <ul>
        <li v-for="item in dones" :key="item.id" @click="handleChangeStatus(item, false)">
          <input type="checkbox">
          <label>{{item.text}}</label>
        </li>
      </ul>
    </div>
  </div>
</template>

<script lang="ts">
  import {reactive, computed} from 'vue'
  import {useRouter} from 'vue-router'
  export default {
     setup(props, context) {
         const state = reactive({
             todoList: [
                 {
                     id: 1,
                     done: false,
                     text: '吃饭'
                 },
                 {
                     id: 2,
                     done: false,
                     text: '睡觉'
                 },
                 {
                     id: 3,
                     done: false,
                     text: '打豆豆'
                 }
             ],
             todo: ''
         })
         const todos = computed(() => {
             return state.todoList.filter(item => !item.done)
         })
         const dones = computed(() => {
             return state.todoList.filter(item => item.done)
         })
         const handleChangeStatus = (item, status) => {
             item.done = status
         }
         const handleAddTodo = () => {
             if (!state.todo) {
                 alert('请输入代办事项')
                 return
             }
             state.todoList.push({
                 text: state.todo,
                 id: Date.now(),
                 done: false
             })
             state.todo = ''
         }
         return {
             state,
             todos,
             dones,
             handleChangeStatus,
             handleAddTodo
         }
     }
  }
</script>

<style scoped>
  .todo-list {
    text-align: center;
  }
  .todo-list ul li {
    list-style: none;
  }
</style>
