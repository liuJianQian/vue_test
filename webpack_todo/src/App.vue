<template>
  <div class="todo-container">
    <div class="todo-wrap">
      <todo-header :add-todo='addTodo'></todo-header>
      <todo-main :todos='todos'></todo-main>
      <todo-footer :delete-todo='deleteTodo'></todo-footer>
    </div>
  </div>
</template>

<script>
  import todoHeader from 'components/header'
  import todoMain from 'components/main'
  import todoFooter from 'components/footer'
  export default {
    data () {
      return {
        todos: [
          {text: '吃饭', state: false},
          {text: '睡觉', state: false},
          {text: '打豆豆', state: false}
        ]
      }
    },
    methods: {
      addTodo (todo) {
        this.todos.unshift(todo)
      },
      deleteTodo (todo) {
        this.todos.$remove(todo)
      }
    },
    events: {
      todo_delete (todo) {
        this.deleteTodo(todo)
      }
    },
    components: {
      todoHeader,
      todoMain,
      todoFooter
    }
  }
</script>

<style>
  /* app */
  .todo-container {
    width: 600px;
    margin: 0 auto;
  }
  .todo-container .todo-wrap {
    padding: 10px;
    border: 1px solid #ddd;
    border-radius: 5px;
  }
</style>
