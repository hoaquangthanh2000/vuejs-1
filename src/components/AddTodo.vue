<template>
    <form>
        <input
            type="text"
            v-model="title"
            
        />
        <button 
            class="add-btn" 
            @click="handleAddTodo"
        >
            Them
        </button>
    </form>
</template>

<script>
import { ref } from 'vue';
// import {v4 as uuidv4 } from 'uuid'
export default {
    name:'Change-todo',
    setup(props,context){
        const title = ref('')
        
        const handleAddTodo = (e) => {
            e.preventDefault();
            const newItem = {
                // id:uuidv4(),
                title:title.value,
                completed:false
            }
            context.emit('add-todo', newItem)
            title.value = ''

        }
        return {
            title,
            handleAddTodo
            
        }
    }
}
</script>

<style scoped>
    from{
        display: flex;
    }

    input[type='text']{
        padding: 5px;
        width: 500px;

    }
    .add-btn{
        padding: 5px;
        width: 100px;
    }
</style>