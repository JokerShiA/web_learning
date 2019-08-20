<template>
  <div class="test">
    <h1>{{ msg }}</h1>
    <!--  -->
    <ul>
      <li v-for="n in evenNumbers" :key="n">{{ n }}</li>
    </ul>
    <input :value="value" v-on:keyup.enter="onEnterUp" v-on:keydown.enter="onEnterDown" />
    <br />
    <!--  -->
    <div id="blog-posts-events-demo" v-if="false">
      <div :style="{ fontSize: postFontSize + 'em' }">
        <sub-post
          v-for="post in posts"
          v-bind:key="post.id"
          v-bind:post="post"
          v-on:enlarge-text="postFontSize += $event"
          v-on:narrow-text="postFontSize -= $event"
        ></sub-post>
      </div>
    </div>

    <!-- v-slot: 缩写# -->
    <test-slot>
      <template v-slot:default="slotProps">{{ slotProps.user.firstName }}</template>
      <template #other="otherSlotProps">{{ otherSlotProps.user.lastName }}</template>
      <template #jiexi="{user}">{{user.firstName + user.lastName }}</template>
      <template v-slot:todo="{ todo }">
        <span v-if="todo.isComplete">✓</span>
        {{ todo.text }}
      </template>
    </test-slot>
    <!--  -->
    <components-edge v-if="true"></components-edge>
    <!--  -->
  </div>
</template>

<script>
import subPost from "./emit.vue";
import testEvent from "./testEvent.vue";
import testSlot from "./testSlot.vue";
import componentsEdge from "./componentsEdge.vue"

export default {
  name: "test",
  components: {
    subPost,
    testEvent,
    testSlot,
    componentsEdge
  },
  props: {
    msg: String
  },
  data() {
    return {
      numbers: [1, 2, 3, 4, 5],
      counter: 0,
      posts: [
        { title: "aa", id: 1 },
        { title: "bb", id: 2 },
        { title: "cc", id: 3 }
      ],
      postFontSize: 1,
      value: 'xxxxxx'
    };
  },
  methods: {
    onEnterUp: function() {
      console.log("enter up");
    },
    onEnterDown: function() {
      console.log("enter down");
    }
  },
  computed: {
    evenNumbers: function() {
      return this.numbers.filter(function(number) {
        return number % 2 === 0;
      });
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
