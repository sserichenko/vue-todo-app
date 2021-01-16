<template>
      <li class="v-todo-item">
          <span :class="{'todo-done': todo.completed}">
              <input type="checkbox" 
              class="item-checkbox"
              v-on:change="todo.completed = !todo.completed"
              >
              <strong>{{todoIndex + 1}}</strong>
              {{todo.title | upperCaseFirst}}
          </span>
          <button 
          class="remove-button"
          @click="removeTodo"
          >&times;</button>
      </li>
</template>

<script>
export default {
    name: 'v-todo-item',
    props: {
        todo: {
            type: Object,
            default: () => {},
            required: true
        },
        todoIndex: {
            type: Number,
            default: 0
        }
    },
    filters: {
        upperCaseFirst(value){
            return value.charAt(0).toUpperCase() + value.slice(1)
        }
    },
    data(){
        return {

        }
    },
    computed: {},
    methods: {
        removeTodo(todo){
            this.$emit('removeTodo', todo.id)
        }
    }

}
</script>

<style scoped>
.v-todo-item{
    padding: 8px 16px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    align-content: center;
    border: 1px solid #cecece;
    margin-bottom: 4px;
}
.item-checkbox{
    margin-right: 10px;
}
.remove-button{
    width: 30px;
    height: 30px;
    border-radius: 50%;
    border: 1px solid grey;
    background: crimson;
    color: #fff;
}
.todo-done{
    text-decoration: line-through;
}
</style>