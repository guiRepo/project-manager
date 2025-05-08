<script setup lang="ts">
import CardProject from '~/components/CardProject.vue';

const listProjects = [
  {
    projectName: 'Bruce',
    client: 'batman',
    beginDate: '11/11/1111',
    endDate: '12/12/1212',
    cover: new URL('@/assets/images/proj.png', import.meta.url).href 
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
	<main class="container px-4 md:px-8">
    <div class="header">
      <h1 class="list-project-title">Projeto  <span class="number-projects">({{ listProjects.length }})</span></h1>
    </div>
	<section>
    
    <div class="grid gap-4 grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 xl:grid-cols-5">
      <CardProject
      v-for="(projeto, index) in listProjects"
      :key="index"
      :title="projeto.projectName"
      :sub-title="projeto.client"
      :begin-date="projeto.beginDate"
      :end-date="projeto.endDate"
      :cover="projeto.cover"
    />
  </div>
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
  .header {
    margin-bottom: 20px;
  }
</style>