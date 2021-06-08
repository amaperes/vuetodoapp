<template>
  <div class="card">
    <input 
      type='text' 
      v-model='todo'
      class="card__input"
      @keydown.enter.prevent="addTodo"
      placeholder="Create a new todo..."
    />
  </div>
</template>

<script>
export default {
  name: 'TodoInput',
  data() {
    return {
      todo: '',
    }
  },
  methods: {
    addTodo() {
      this.$emit("add-todo", this.todo);
      this.todo = '';
    },
  },
}

</script>
<style lang="scss" scoped>
@import "../../assets/scss/sections/input.scss";
</style>
