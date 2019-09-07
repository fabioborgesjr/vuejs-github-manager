<template>
  <div>
    <label for="basic-url">Your GitHub username</label>
    <div class="input-group mb-3">
      <div class="input-group-prepend">
        <span
          class="input-group-text"
          id="basic-addon3"
        >
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
        v-model="value"
      />
    </div>
  </div>
</template>

<script>
import Axios from "axios";

export default {
  data() {
    return {
      URL: "https://api.github.com",
      value: ""
    };
  },
  methods: {
    async handleChange(event) {
      const value = this.value,
        regAllowed = /^[a-z\d](?:[a-z\d]|-(?=[a-z\d])){0,38}$/i;

      if (event.key === "Enter") {
        if (regAllowed.test(value)) {
          try {
            let { status, data } = await Axios.get(
              `${this.URL}/users/${value}/repos`
            );

            this.$emit("updateContainer", { status, data });
          } catch (error) {
            this.$emit("updateContainer", {
              status: 404,
              data: []
            });
          }

          this.value = "";
        }
      }
    }
  }
};
</script>

<style>
</style>