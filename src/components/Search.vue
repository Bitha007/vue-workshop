<template>
  <div class="search">
    <input v-model="title" type="text" class="form-control" placeholder="Search by title" />
  </div>
</template>

<script>
export default {
  name: "Search",
  data() {
    return {
      title: ""
    };
  },
  watch: {
    async title(value) {
      this.$emit("title", value);
    }
  }
};
</script>

<style scoped lang="scss">
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