<template>
  <div>
    <h1>{{ message }}</h1>
    <Input/>
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