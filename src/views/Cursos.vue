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
          <li v-for="(lista, index) in api.cursos" :key="index">
            <h2>{{ lista[0] }}</h2>
          </li>
        </ul>
      </div>
    </transition>
  </div>
</template>

<script>
import fetchData from "@/mixins/fetchData.js";

export default {
  name: "cursos",
  mixins: [fetchData],
  created() {
    this.fetchData("/cursos");
  },
};
</script>
