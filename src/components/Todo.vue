<template>
  <AddTodo
    @add-todo="AddTodoList"
  />
  <TodoItem 
    v-for="todo in abc" 
    v-bind:key="todo.id" 
    v-bind:todoProps="todo" 
    @item-completed="handleCompleted"
    @delete-item="handleDelete"
  />

</template>

<script>
  import { ref } from 'vue';
  import TodoItem from './TodoItem.vue'
  import AddTodo from './AddTodo.vue'
  import axios from 'axios'

  export default {
    name: "todo-s",
    components: { TodoItem, AddTodo },
    setup() {
        const todos = ref([]);

        const getAllTodo = async() => {
          try {
            const res = await axios.get('https://jsonplaceholder.typicode.com/todos?_limit=10')
            todos.value = res.data
          } 
          catch (error) {
            console.log(error)
          }
        }
        getAllTodo()


        const handleCompleted = (id) => {
          todos.value = todos.value.map( todo => {
            if(todo.id === id){
              todo.completed = !todo.completed
            }
            return todo
          } )
        }

        const handleDelete = async id => {
          try {
            await axios.delete( `https://jsonplaceholder.typicode.com/todos/${id}`)
            todos.value = todos.value.filter( todo => todo.id !== id )

          } catch (error) {
            console.log(error)
          }
        }

        const AddTodoList = async newTodo => {
          try {
            const res = await axios.post('https://jsonplaceholder.typicode.com/todos', newTodo)
            todos.value.push(res.data)
          } catch (error) {
            console.log(error)
          }
        }

        return {
            abc: todos,
            handleCompleted,
            handleDelete,
            AddTodoList,
        };
    },
}
</script>

<style>

</style>