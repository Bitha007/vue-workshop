<template>
  <div id="app">
    Getting Started with Vuejs
    <HelloWorld v-bind:msg="msg" />
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld";
export default {
  name: "app",
  components: {
    HelloWorld
  },
  data() {
    return {
      msg: "Life is beautiful Isn`t it?"
    };
  }
};
</script>

<style lang="scss">
@import "./styles/main.scss";

#app {
  margin-top: 60px;
  text-align: center;
}
</style>
