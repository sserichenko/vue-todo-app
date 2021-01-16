<template>
  <form class="v-add-todo"
   @submit.prevent="onSubmit"
   >
    <input 
    class="add-todo-input"
    type="text"
    v-model="title"
    >
    <button 
    type="submit"
    >Create todo</button>
  </form>
</template>

<script>
export default {
    name: 'v-add-todo',
    data(){
        return{
            title: ''
        }
    },
    methods: {
        onSubmit(){
            if(this.title.trim()){
                const newTodo = {
                    id: Date.now(),
                    title: this.title,
                    completed: false
                }
                this.$emit('addTodo', newTodo)
                this.title = '';
            }
        }
    }


}
</script>

<style>
.v-add-todo{
    display: flex;
}
.add-todo-input{
    width: 400px;
    margin-right: 20px;
}
</style>