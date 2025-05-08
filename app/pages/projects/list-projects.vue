<script setup lang="ts">
import CardProject from '~/components/CardProject.vue';

const listProjects = [
  {
    projectName: 'Bruce',
    client: 'batman',
    beginDate: '11/11/1111',
    endDate: '12/12/1212',
    cover: ''
  },  
  {
    projectName: 'Clark',
    client: 'superman',
    beginDate: '11/11/1111',
    endDate: '12/12/1212',
    cover: ''
  },
  {
    projectName: 'Diana',
    client: 'wonderwoman',
    beginDate: '11/11/1111',
    endDate: '12/12/1212',
    cover: ''
  },
  {
    projectName: 'Hal',
    client: 'greenlantern',
    beginDate: '11/11/1111',
    endDate: '12/12/1212',
    cover: ''
  },
  {
    projectName: 'Bart',
    client: 'flash',
    beginDate: '11/11/1111',
    endDate: '12/12/1212',
    cover: ''
  }
]
</script>

<template>
	<main class="container">
		<h1 class="list-project-title">Projeto  <span class="number-projects">({{ listProjects.length }})</span></h1>

	<section>
    <CardProject />
	</section>
	</main>
</template>

<style scoped>
	.list-project-title {
		color: #1F1283;
		font-family: Encode Sans Semi Expanded;
		font-weight: 600;
		font-size: 24px;
		margin-top: 15px;
	}
	.container {

		max-width: 100%; 

	}
  .number-projects {
    color: #695CCD;
		font-weight: 600;
		font-size: 17px;
		margin-top: 5px;
    vertical-align: middle;
  }
</style>