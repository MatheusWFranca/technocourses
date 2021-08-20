<template>
  <div>
    <div v-if="loading">
      <PageLoading />
    </div>
    <transition>
      <div v-if="api">
        <h1>{{ api.titulo }}</h1>
        <p>{{ api.descricao }}</p>
        <ul>
          <li v-for="(contatos, index) in api.contato" :key="index">
            <p class="dados">{{ index }}: {{ contatos }}</p>
          </li>
        </ul>
        <router-link tag="button" class="btn-cursos" to="/"
          >Whatsapp</router-link
        >
      </div>
    </transition>
  </div>
</template>

<script>
import fetchData from "@/mixins/fetchData.js";

export default {
  name: "contato",
  mixins: [fetchData],
  created() {
    this.fetchData("/contato");
  },
};
</script>

<style scoped>
.dados {
  color: #1c1c1c;
}
</style>