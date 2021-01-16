<template>
  <div>
        <h2>Our Todos</h2>
        <hr>
        <router-link to="/">Home</router-link>
        <hr>
        <v-add-todo
        @addTodo="addTodo"
        />
        <br>
        <select v-model="filter">
            <option value="all">All</option>
            <option value="completed">Completed</option>
            <option value="not-completed">Not completed</option>
        </select>
        <hr>
        <v-loader v-if="isLoading"/>
        <v-todo-list 
        v-else-if="filteredTodos.length"
        :todos="filteredTodos"
        @removeTodo="removeTodo"
        
        />
        <p v-else>There are no todos</p>
    </div>
</template>

<script>
import VAddTodo from '../components/v-add-todo'
import VTodoList from '../components/v-todo-list'
import VLoader from '../components/v-loader.vue'


export default {
  name: 'Todos',
  data(){
    return{
      todos: [],
      isLoading: true,
      filter: 'all'
    }
  },
  components: {
    VLoader,
    VTodoList,
    VAddTodo
  },
//   watch: {
//       filter(value){
//           console.log('value', value);
//       }
//   },
computed: {
    filteredTodos(){
        if(this.filter === 'all'){
            return this.todos
        }
        if(this.filter === 'completed'){
            return this.todos.filter(todo => todo.completed)
        }
        if(this.filter === 'not-completed'){
            return this.todos.filter(todo => !todo.completed)
        }else{
            return this.todos
        }
    }
},
  methods: {
    removeTodo(id){
      this.todos = this.todos.filter((todo) => todo.id !== id)
    },
    addTodo(todo){
      this.todos.push(todo);
    }
  },
  mounted(){
    fetch('https://jsonplaceholder.typicode.com/todos?_limit=5')
    .then((response) => response.json())
    .then((json) => {
      this.todos = json
      setTimeout(() => {
          this.isLoading = false;
      })
    })
  }
}
</script>


<style>

</style>