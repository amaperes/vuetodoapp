<template>
  <todo-input @add-todo="addNewTodo"/>
  <div class="todo__wrapper">
    <todo-item
      v-for="todo in filteredTodos"
      :key="todo.id"
      :id="todo.id"
      :name="todo.name"
      :isChecked="todo.isChecked"
      @check-todo="checkTodo"
      @delete-todo="deleteTodo"
    ></todo-item>
    <div class="todo__footer">
      <span class="todo__footer-items"> {{ remainingTodos }} items left</span>
      <div class="todo__footer-tabs">
        <p class="todo__footer-tabs-item" :class="{active: filter=== 'all'}" @click="filter = 'all'">All</p>
        <p class="todo__footer-tabs-item" :class="{active: filter=== 'active'}" @click="filter = 'active'">Active</p>
        <p class="todo__footer-tabs-item" :class="{active: filter=== 'completed'}" @click="filter = 'completed'">Completed</p>
      </div>
      <button class="todo__footer-cta" @click="clearCompleted">Clear Completed</button>
    </div>
  </div>
  <p class="todo__instruction">Drag and drop to reorder list</p>
</template>

<script>
import TodoInput from './main/TodoInput.vue';
import TodoItem from './main/TodoItem.vue';

export default {
  name: 'TodoApp',
  components: {
    TodoInput,
    TodoItem,
  },
  data() {
    return {
      todos: [
         {
          id:0,
          name: "Complete Online Javascript Course",
          isChecked: false
        },
        {
          id:1,
          name: "Jog around the pack 3x",
          isChecked: false
        },
        {
          id:2,
          name: "10 mins meditation",
          isChecked: true
        },
        {
          id:3,
          name: "Read for 1 hour",
          isChecked: false
        },
        {
          id:4,
          name: "Pick up groceries",
          isChecked: false
        },
        {
          id:5,
          name: "Complete Todo App on Frontend Mentor",
          isChecked: false
        }
      ],
      filter: 'all',
      index: 6
    }
  },
  methods: {
    addNewTodo(newTodo) {
      debugger
      this.todos.unshift({
        id: this.index,
        name: newTodo,
        isChecked: false,
      });
      this.index++
    },
    checkTodo(payload) {
      this.todos.map((item) => {
        if (item.id == payload.id) item.isChecked = !item.isChecked;
      });
    },
    deleteTodo(index) {
      const removeIndex =  this.todos.map(item => item.id).indexOf(index)
      this.todos.splice(removeIndex, 1)
    },
    clearCompleted() {
      this.todos = this.todos.filter(todo =>!todo.isChecked);
    }
  },
  computed: {
    remainingTodos() {
      switch(this.filter) {
          case "all":
            return this.todos.filter(todo => !todo.isChecked).length;
          case "active":
            return this.todos.filter(todo => !todo.isChecked).length;
          case "completed":
            return 0;
        }
      
    },
    filteredTodos() {
        switch(this.filter) {
          case "all":
            return this.todos
          case "active":
            return this.todos.filter(todo => !todo.isChecked);
          case "completed":
           return this.todos.filter(todo => todo.isChecked);
        }
    }
  }
}

</script>
<style lang="scss" scoped>
@import "../assets/scss/sections/app.scss";
</style>
