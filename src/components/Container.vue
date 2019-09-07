<template>
  <div>
    <div
      v-for="(value, index) in data"
      :key="index"
      :data-test="dataTest"
      class="card"
    >
      <h5 class="card-title">Repositório</h5>
      <div class="card-body">
        <div v-if="message !== ''">{{message}}</div>
        <div v-else>
          <p>Nome: {{value.name}}</p>
          <p>Link: {{value.html_url}}</p>
          <p>Número de stars: {{value.stargazers_count}}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    data: Array,
    status: Number
  },
  data() {
    return {
      message: "",
      dataTest: ""
    };
  },
  methods: {
    fill() {
      var me = this,
        props = me._props;

      if (props.status === 404) {
        me.dataTest = "nao-encontrado";
        me.message = "Usuário não encontrado";
      } else if (Object.keys(props.data[0]).length === 0) {
        me.dataTest = "sem-repositorios";
        me.message = "O usuário não tem nenhum repositório";
      } else {
        me.dataTest = "repositorio";
      }
    }
  },
  created() {
    var me = this;

    me.fill();
  },
  beforeUpdate() {
    var me = this;

    if (me.message !== "") me.message = "";

    me.fill();
  }
};
</script>

<style>
</style>