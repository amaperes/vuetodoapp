<template>
   <header class="header">
      <h1 class="header__title">todo</h1>
      <button class="header__button" @click.prevent="darkModeSwitch">
        <img src="../../assets/images/icon-moon.svg" class="header__button-icon header__button-icon--sun" alt="">
        <img src="../../assets/images/icon-sun.svg" class="header__button-icon header__button-icon--moon" alt="">
      </button>
    </header>
</template>

<script>

export default {
  name: 'TodoHeader',
  data() {
    return {
      darkMode: false,
    }
  },
  methods: {
    darkModeSwitch() {
      this.darkMode = !this.darkMode;
      const html = document.querySelector('html');
      const theme = this.darkMode === false ? "light" : "dark"
      html.dataset.theme = `theme-${theme}`;
    }
  }
}

</script>
<style lang="scss">
@import "../../assets/scss/sections/header.scss";
</style>
