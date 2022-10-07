<template>
  <p :class="todoProps.completed ? 'is-completed' : '' ">
    <input 
        type="checkbox" 
        :checked="todoProps.completed"
        @:change="handChange"
    />
    {{ todoProps.title }}
    <button 
        class="dele" 
        @click="deleteItem"
    >
        delete
    </button>
</p>
</template>

<script>
// import { ref } from 'vue';

export default {
    name:"todo-item",
    props: [ 'todoProps' ],
    setup(props,context){
        const handChange = () => {
            context.emit('item-completed', props.todoProps.id)
        }
        const deleteItem = () => {
            context.emit('delete-item', props.todoProps.id)
        }


        return {
            handChange,
            deleteItem
        } 
    }
}
</script>

<style>
    .is-completed{
        text-decoration: line-through;
    }
    .dele{
        background: red;
        color: black;
        border-radius: 3px;
        cursor: pointer;
        float: right;
    }
</style>