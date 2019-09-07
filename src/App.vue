<template>
  <div>
    <h1>{{ message }}</h1>
    <Input @updateContainer="updateContainer" />
    <div v-if="status !== 0">
      <Container :data="data" :status="status"/>
    </div>
  </div>
</template>

<script>
import Input from "./components/Input";
import Container from "./components/Container";

export default {
  data: () => ({
    message: "GitHub Manager",
    data: [],
    status: 0
  }),
  components: {
    Input,
    Container
  },
  methods: {
    updateContainer(values) {
      const { status, data } = values;

      this.status = status;

      if (data.length > 0) {
        this.data = data;
      } else {
        this.data = [{}];
      }
    }
  }
};
</script>