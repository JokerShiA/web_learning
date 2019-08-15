<template>
  <div class="test">
    <h1>{{ msg }}</h1>
    <button v-on:click="reverseMessage">反转消息</button>
    <ul>
      <li v-for="n in evenNumbers" :key="n">{{ n }}</li>
    </ul>
    <input v-on:keyup.enter="onEnterUp" v-on:keydown.enter="onEnterDown" />
    <br />

    <div id="blog-posts-events-demo">
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

  </div>
</template>

<script>
import subPost from "./sub.vue";

export default {
  name: "test",
  components: {
    subPost
  },
  props: {
    msg: String
  },
  data() {
    return {
      numbers: [1, 2, 3, 4, 5],
      counter: 0,
      posts:[{title: 'aa', id:1},{title: 'bb', id:2},{title: 'cc',id:3}],
      postFontSize: 1
    };
  },
  methods: {
    reverseMessage: function() {
      this.msg = this.msg
        .split("")
        .reverse()
        .join("");
    },
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
