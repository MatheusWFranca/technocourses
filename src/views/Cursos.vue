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
          <li v-for="curso in api.cursos" :key="curso.id">
            <router-link
              :to="{ name: 'curso', params: { curso: curso.id } }"
              tag="h2"
            >
              {{ curso.nome }} - {{ curso.totalAulas }} aulas |
              {{ curso.horas }} horas
            </router-link>
            <p>{{ curso.descricao }}</p>
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
