<template>
  <div>
    <span>
      <slot v-bind:user="user">{{ user.lastName }}</slot>
      <br />
      <slot name="other" v-bind:user="user">{{ user.lastName }}</slot>
      <br />
      <slot name="jiexi" v-bind:user="user"></slot>
    </span>

    <ul>
      <li v-for="todo in filteredTodos" v-bind:key="todo.id">
        <slot name="todo" v-bind:todo="todo"><!-- 后备内容 --></slot>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: {},
  data() {
    return {
      user: { firstName: "2333", lastName: "456" },
      filteredTodos: [
        { id: 1, text: "a", isComplete: true },
        { id: 2, text: "b", isComplete: false },
        { id: 3, text: "c", isComplete: true }
      ]
    };
  }
};
</script>

<style>
</style>