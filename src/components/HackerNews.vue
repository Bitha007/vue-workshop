<template>
  <div class="container">
    <div class="card">
      <div class="heading">
        <h4 class="title">Netflix Ratings</h4>
      </div>
      <Search @title="handleTitleChange" />
      <Stories :stories="stories" :loading="loading"   />
    </div>
  </div>
</template>

<script>
import axios from "axios";
import Stories from "./Stories";
import Search from "./Search";
export default {

  name: "HackerNews",
  data: function() {
    return {
      loading: true,
      error: null,
      stories: [],
    };
  },
  created: async function() {
    this.getData();
  },
  methods: {
    async getData(title ) {
      this.loading = true;
      try {
        const response = await axios.get(
          "http://hn.algolia.com/api/v1/search",
          {
            params: {
              query: title
            }
          }
        );
        this.stories = response.data.hits;
      } catch (error) {
        this.error = error.message;
      } finally {
        this.loading = false;
      }
    },
    async handleTitleChange(title){
      this.getData(title);
    }
  },
  watch: {
    title: function(value) {
      console.log(value)
      this.getData();
    }
  },
  components:{
    Stories,
    Search
  }
};
</script>

