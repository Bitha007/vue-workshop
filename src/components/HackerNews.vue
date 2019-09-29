<template>
  <div class="container">
    <div class="card">
      <div class="heading">
        <h4 class="title">Netflix Ratings</h4>
      </div>
      <div class="search">
        <input v-model="keyword" type="text" class="form-control" placeholder="Search by title" />
      </div>
      <div class="content">
        <div>
          <p v-if="!news.length">Loading news</p>
        </div>
        <div v-for="n in news" :key="n.objectID">
          <div>
            <p></p>
          </div>
          <ul class="list">
            <li v-if="n.title && n.author">
              <a :href="n.url">{{n.title}}</a>
              <span>By: {{n.author}}</span>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "HackerNews",
  data() {
    return {
      news: [],
      keyword: "",
      count: 0
    };
  },
  async created() {
    try {
      let url = "http://hn.algolia.com/api/v1/search?query=" + this.keyword;
      const res = await axios.get(url);
      this.news = res.data.hits;
    } catch (error) {
      console.log(error);
    }
  },
  watch: {
    async keyword(value) {
      this.news = [];
      await setTimeout(console.log(this.count), 5000);
      this.count++;
      console.log(this.count);
      try {
        let url = "http://hn.algolia.com/api/v1/search?query=" + value;
        const res = await axios.get(url);
        this.news = res.data.hits;
      } catch (error) {
        console.log(error);
      }
    }
  }
};
</script>

<style scoped lang="scss">
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
.search {
  margin-bottom: 24px;
  .form-control {
    background-color: transparent;
    border: none;
    border-bottom: 1px solid #ced4da;
    border-radius: 0;
    outline: 0;
    box-shadow: none;
    padding: 6px 0;
    width: 100%;
  }
}
</style>