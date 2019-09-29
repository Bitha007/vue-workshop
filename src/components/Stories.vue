<template>
  <div class="content">
    <div v-if="loading">
      <p>Loading news</p>
    </div>
    <div v-else>
      <div v-if="error">
        <p>{{error}}</p>
      </div>
      <ul v-else class="list">
        <li v-for="(news, index) in stories" :key="index">
          <template v-if="news.title">
            <a :href="news.url">{{news.title}}</a>
            <span>By: {{news.author}}</span>
          </template>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: "Stories",
  props:{
    stories:Array, 
    loading:Boolean,
    error:String
  }
};
</script>

<style  scoped lang="scss">
.container {
  margin: 0 auto;
  max-width: 768px;
}

.card {
  box-shadow: 0 2px 3px rgba(10, 10, 10, 0.1), 0 0 0 1px rgba(10, 10, 10, 0.1);
  padding: 24px;
}

.list {
  > li {
    &:not(:last-child) {
      margin-bottom: 18px;
    }
    > a {
      color: #0a5b8c;
      display: block;
      margin-bottom: 6px;
    }

    > span {
      color: rgba(#3b4242, 0.7);
      font-size: 12px;
    }
  }
}

.btn {
  color: #fff;
  cursor: pointer;
  background-color: #117a8b;
  border-color: #10707f;
  border: 1px solid transparent;
  padding: 6px 12px;
  border-radius: 6px;
  transition: all 0.1s ease-in;
  &:hover {
    background-color: #138496;
    border-color: #117a8b;
  }
}

.heading {
  margin-bottom: 12px;

  .title {
    font-size: 18px;
    font-weight: 600;
  }
}
  
</style>