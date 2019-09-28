<template>
  <div class="container">
    <div class="card">
      <div class="filters">
        <div>
          <h4 class="title">Netflix Ratings</h4>
          <div class="actions">
            <button class="btn" @click="highestRated">Lowest rated</button>
            <button class="btn" @click="lowestRated">Highest rated</button>
          </div>
        </div>
        <div class="search">
          <input
            v-model="keyword"
            type="text"
            class="form-control"
            placeholder="Search by title"
          />
        </div>
      </div>
      <div class="content">
        <table class="table">
          <thead v-for="(column, index) in columns" :key="index">
            <th>{{column}}</th>
          </thead>
          <tbody>
            <tr v-for="ratingInfo in filteredData" :key="ratingInfo.title">
              <td>{{ratingInfo.title}}</td>
              <td>{{ratingInfo.rating}}</td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "NetflixRatings",
  data: function() {
    return {
      keyword: "",
      columns: ["title", "rating"],
      ratingsInfo: [
        { title: `Grey's Anatomy`, rating: 98 },
        { title: `Prison Break`, rating: 98 },
        { title: `How I Met Your Mother`, rating: 94 },
        { title: `Supernatural`, rating: 95 },
        { title: `Breaking Bad`, rating: 97 },
        { title: `The Vampire Diaries`, rating: 91 },
        { title: `The Walking Dead`, rating: 98 },
        { title: `Pretty Little Liars`, rating: 96 },
        { title: `Once Upon a Time`, rating: 98 },
        { title: `Sherlock`, rating: 95 },
        { title: `Death Note`, rating: 77 },
        { title: `Naruto`, rating: 88 },
        { title: `Arrow`, rating: 96 },
        { title: `Black Mirror`, rating: 80 },
        { title: `The Originals`, rating: 74 },
        { title: `The 100`, rating: 97 },
        { title: `Masha and the Bear`, rating: 81 },
        { title: `Hunter X Hunter`, rating: 57 },
        { title: `Marvel's Luke Cage`, rating: 95 },
        { title: `Marvel's Iron Fist`, rating: 98 }
      ]
    };
  },
  methods: {
    highestRated: function() {
      this.ratingsInfo.sort((a, b) => (a.rating > b.rating ? 1 : -1));
    },
    lowestRated: function() {
      this.ratingsInfo.sort((a, b) => (a.rating > b.rating ? -1 : 1));
    }
  },
  computed: {
    filteredData: function() {
      return this.ratingsInfo.filter(info => {
        let name = info.title.toLowerCase();
        return name.includes(this.keyword.toLowerCase());
      });
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

.table {
  width: 100%;
  margin-bottom: 24px;
  thead {
    th {
      border-bottom: 2px solid #ccc;
      text-align: left;
      font-weight: 600;
    }
  }
  td,
  th {
    padding: 0.75rem;
    vertical-align: top;
    border-top: 1px solid #dee2e6;
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

.filters {
  > div {
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin-bottom: 12px;
  }

  margin-bottom: 18px;

  .title {
    font-size: 18px;
    font-weight: 600;
  }

  .btn {
    &:first-child {
      margin-right: 12px;
    }
  }

  .search {
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
}
</style>
