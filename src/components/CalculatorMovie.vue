<template>
  <div class="container">
    <div class="card calculator">
      <div class="header">
        <h4 class="title">Display sum between two numbers</h4>
      </div>
      <div class="content">
        <div class="form-group">
          <input
            type="number"
            class="form-control"
            placeholder="First Number"
            v-model.number="first"
          />
        </div>
        <div class="form-group">
          <input
            type="number"
            class="form-control"
            placeholder="Second Number"
            v-model.number="second"
          />
        </div>

        <div class="form-group">
          <p>The sum is {{first + second}}</p>
        </div>
      </div>
    </div>

    <div class="card movie">
      <div class="header">
        <h4 class="title">Which is your most anticipated movie ?</h4>
      </div>

      <div class="content">
        <div class="form-group">
          <select v-model="selected" class="form-control">
            <option>Doctor Strange in the Multiverse of Madness</option>
            <option>Thor: Love and Thunder</option>
            <Option>Joker</Option>
          </select>
        </div>
        <div class="form-group">
          <p v-if="selected" >My most anticipated movie is: {{selected}} </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "CalculatorMovie",
  data() {
    return {
      first: "",
      second: "",
      selected:"Doctor Strange in the Multiverse of Madness"
    };
  },
  methods: {

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

.calculator {
  margin-bottom: 24px;
}

.form-group {
  &:not(:last-child) {
    margin-bottom: 18px;
  }
}

.form-control {
  display: block;
  width: 100%;
  padding: 0.375rem 0.75rem;
  font-size: 1rem;
  line-height: 1.5;
  color: #495057;
  background-color: #fff;
  background-clip: padding-box;
  border: 1px solid #ced4da;
  border-radius: 0.25rem;
  transition: border-color 0.15s ease-in-out, box-shadow 0.15s ease-in-out;
}
</style>
