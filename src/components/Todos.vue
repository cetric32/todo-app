<template>
<div>
    <h1>Todos</h1>
   
        <div v-for="(todo, index) in todos" :key="index">
            <Todo-item 
            :todo='todo'
            @del-todo="$emit('del-todo',todo.id)"
            ></Todo-item>
        </div>
</div>  
</template>

<script>
import TodoItem from './TodoItem'

export default {
    name: "Todos",
    props:{
        todos:Array
    },
    components:{
        TodoItem
    }

}
</script>

<style scoped>

</style>