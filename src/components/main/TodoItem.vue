<template>
  <div class="todo">
    <li class="todo__item" :class="{ completed: isChecked }" id="id" @click.prevent="checkTodo">
      <input class="todo__item-input" type="checkbox" data-index="0" id="id">
      <label for="id" class="todo__label">
        <span class="todo__label-text">{{ name }}</span>
        <span class="todo__span"><img class="todo__check" src="../../assets/images/icon-check.svg" alt="Check icon" /></span>
      </label>
      <button data-index="0" data-deletebtn="" aria-label="Remove todo" class="todo__deleteBtn" @click.prevent="deleteTodo">
        <img
          class="todo__deleteBtn-icon"
          src="../../assets/images/icon-cross.svg"
          alt="Cross icon"
        />
      </button>
    </li>
  </div> 
</template>

<script>
export default {
  name: 'TodoInput',
  props: {
    id: {
      type: Number,
      required: true
    },
    name: {
      type: String,
      required: true
    },
    isChecked: {
      type: Boolean,
      required: true,
    }
  },
  methods: {
    checkTodo() {
      this.$emit("check-todo", {id: this.id});
    },
    deleteTodo() {
      this.$emit("delete-todo", this.id);
    },
  },
}

</script>
<style lang="scss" scoped>
@import "../../assets/scss/sections/item.scss";
</style>
