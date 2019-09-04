<template>
  <div>
    <i class="fas fa-coffee"></i>
    <font-awesome-icon icon="user-secret" />
    <h1>{{ message }}</h1>
    <input/>
  </div>
</template>

<script>
import Input from "./components/Input";

export default {
  data: () => ({
    message: "GitHub Manager"
  }),
  components: {
    Input
  }
};
</script>