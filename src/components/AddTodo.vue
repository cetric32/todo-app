<template>
  <div>
      <form @submit.prevent="addTodo">
          <input type="text" 
          name="title"
          placeholder="Add Todo..."
          v-model="title">
          <input type="submit" value="Submit" class="btn">
      </form>
  </div>
</template>

<script>
import uuid from 'uuid';

export default {
    name:'AddTodo',
    data(){
        return {
            title: null 
        }
    },
    methods: {
        addTodo(e){
            e.preventDefault();
            const newTodo = {
                id: uuid.v4(),
                title: this.title,
                completed: false
            }
            //reset title
            this.title = null;
            //send up to parent
            this.$emit('add-todo', newTodo);
        }
    }

}
</script>

<style scoped>

</style>