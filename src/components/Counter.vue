<template>
  <div class="container">
    <div class="card">
      <div class="heading">
        <h4 class="title">Increment or decrement a number</h4>
      </div>
      <div class="content">
        <button type="button" v-on:click="num++" class="btn">+</button>
        <span class="counter" >{{num}}</span>
        <button type="button" v-on:click="num--" class="btn">-</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name:"Counter",
  data(){
    return{
      num:0
    }
  }
};
</script>


<style scoped lang="scss">
.container {
  margin: 0 auto;
  max-width: 768px;
}
.title {
  font-size: 18px;
  font-weight: 600;
  margin-bottom: 18px;
}
.card {
  box-shadow: 0 2px 3px rgba(10, 10, 10, 0.1), 0 0 0 1px rgba(10, 10, 10, 0.1);
  padding: 24px;
}

.btn {
  color: #fff;
  cursor: pointer;
  background-color: #007bff;
  border-color: #007bff;
  padding: 6px 12px;
  font-size: 18px;
  font-weight: 600;
  border-radius: 6px;
  transition: all 0.1s ease-in;

  &:hover {
    background-color: #0069d9;
    border-color: #0062cc;
  }
}

.counter {
  margin: 0 12px;
  font-size: 18px;
  font-weight: 600;
}
</style>