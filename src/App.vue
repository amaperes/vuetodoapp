<template>
  <div>
    <todo-wrapper/>
  </div>
  <div class="attribution">
    Challenge by <a href="https://www.frontendmentor.io?ref=challenge" target="_blank">Frontend Mentor</a>
    Coded by <a href="https://github.com/amaperes">A.P.</a>
  </div>
</template>

<script>
import TodoWrapper from './components/TodoWrapper.vue';

export default {
  name: 'App',
  components: {
    TodoWrapper,
  },
  mounted() {
    const html = document.querySelector('html');
    html.dataset.theme = `theme-light`;
  }
}
</script>

<style lang="scss">
@import "./assets/scss/style.scss";
.attribution { 
  font-size: 11px;
  color: $c-blue-grayish-dark;
  text-align: center;
  //position: fixed;
  bottom: 0;
  width: 100%; 
}
</style>
