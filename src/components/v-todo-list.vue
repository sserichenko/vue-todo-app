<template>
  <div class="v-todo-list">
    <ul class="todo-list">
        <v-todo-item 
        v-for="(todo, index) in todos"
        :todoIndex="index"
        :key="todo.id"
        :todo="todo"
        @removeTodo="removeTodo(todo.id)"
        />
    </ul>
  </div>
</template>

<script>
import vTodoItem from './v-todo-item.vue'
export default {
    name: 'v-todo-list',
    components: { vTodoItem },
    props: {
        todos: {
            type: Array,
            default: () => []
        }
    },
    data(){
        return {

        }
    },
    computed: {},
    methods: {
        removeTodo(id){
            this.$emit('removeTodo', id)
        }
    }

}
</script>

<style scoped>
    .todo-list{
        list-style: none;
        margin: 0;
        padding: 0;
    }
</style>