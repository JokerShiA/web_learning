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
        <!--
    我们为每个 todo 准备了一个插槽，
    将 `todo` 对象作为一个插槽的 prop 传入。
        -->
        <slot name="todo" v-bind:todo="todo">
          <!-- 后备内容 -->
          {{ todo.text }}
        </slot>
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