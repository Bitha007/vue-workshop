<template>
  <div>
    HelloWorld
    <div>{{msg}}</div>
  </div>
</template>
<script>
export default {
  name: "HelloWorld",
  props: { msg: String }
};
</script>
