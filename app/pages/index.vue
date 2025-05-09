<script setup>
import ListProjects from './projects/list-projects.vue';
import ProjectNotFound from './projects/project-not-found.vue';

const hasProjects = ref(false)

onMounted(() => {
  const lista = JSON.parse(localStorage.getItem('allProjects') || '[]');
  hasProjects.value = lista.length > 0;
})
</script>

<template>
  <ListProjects v-if="hasProjects" />
  <ProjectNotFound v-else />
</template>

<style scoped>
</style>