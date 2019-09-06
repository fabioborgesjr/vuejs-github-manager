<template>
  <div>
    <label for="basic-url">Your GitHub username</label>
    <div class="input-group mb-3">
      <div class="input-group-prepend">
        <span class="input-group-text" id="basic-addon3">
          <font-awesome-icon icon="user-secret" />
        </span>
      </div>
      <input
        type="text"
        class="form-control"
        id="basic-url"
        aria-describedby="basic-addon3"
        v-on:keyup="handleChange"
        data-test="entrada"
      />
    </div>
  </div>
</template>

<script>
import Axios from 'axios';

export default {
  data() {
    return {
      URL: "https://api.github.com",
      data: []
    };
  },
  methods: {
    async handleChange(event) {
      const value = event.target.value,
        regAllowed = /^[\w]+-?[\w]*$/g;

      if (event.key === "Enter") {
        if (regAllowed.test(value)) {
          let data;
          data = { data } = await Axios.get(`${this.URL}/users/${value}/repos`);
          console.log(data)
        }
      }
    }
  }
};
</script>

<style>
</style>