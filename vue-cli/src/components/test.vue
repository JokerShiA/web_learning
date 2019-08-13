<template>
  <div class="test">
    <h1>{{ msg }}</h1>
    <!-- <button v-on:click="reverseMessage">反转消息</button> -->
    <p>Original message: "{{ msg }}"</p>
    <p>Computed reversed message: "{{ reversedMessage }}"</p>
  </div>
</template>

<script>
export default {
  name: "test",
  props: {
    msg: String
  },
  data () {
    return {
    }
  },
  // methods: {
  //   reverseMessage: function () {
  //     this.msg = this.msg.split('').reverse().join('')
  //   }
  // }
  computed: {
    // 计算属性的 getter
    reversedMessage: function () {
      // `this` 指向 vm 实例
      return this.msg.split('').reverse().join('')
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
