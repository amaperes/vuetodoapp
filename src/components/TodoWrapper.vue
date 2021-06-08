<template>
  <div class="background">
    <span class="background__img background__img--light"/>
    <span class="background__img background__img--dark"/>
  </div>
  <div class="main-wrapper">
    <todo-header />
    <todo-app />
  </div>
  
</template>

<script>
import TodoHeader from './main/TodoHeader.vue';
import TodoApp from './TodoApp.vue';

export default {
  name: 'TodoWrapper',
  components: {
    TodoHeader,
    TodoApp
  },
}

</script>
<style lang="scss" scoped>
@import "../assets/scss/sections/wrapper.scss";
</style>

