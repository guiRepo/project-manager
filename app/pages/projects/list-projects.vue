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

const value = ref(true)

const itemsSelect = ref(['Ordem alfabética', 'Iniciados mais recentes', 'Prazo mais proximo'])
const valueSelect = ref('')

</script>

<template>
	<main class="container px-4 md:px-8">
    <div class="header">
      <div class="left-side">
        <h1 class="list-project-title">Projeto  <span class="number-projects">({{ listProjects.length }})</span></h1>
      </div>

      <div class="rigth-side">
        <USwitch v-model="value" />
        <span class="favorites-text"> Apenas favoritos</span>
        <select v-model="valueSelect" class="custom-select">
          <option value="" disabled>Selecione uma opção</option>
          <option v-for="(option, index) in itemsSelect" :key="index" :value="option">
            {{ option }}
          </option>
        </select>
        <NuxtLink to="/projects/new">
          <button class="new-project-button">
            <UIcon name="i-lucide-circle-plus" class="new-project-icon" />
            <label class="new-project-button-text">Novo projeto</label>
          </button>
        </NuxtLink>
      </div>
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
        :cover="projeto.cover"/>
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
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    
  }
  .new-project-button {
		background-color: #695CCD;
    width: 184px;
    height: 40px;
    left: 1675px;
    border-radius: 26px;
	}
	.new-project-button-text {
		position: relative;
		font-family: Encode Sans Semi Expanded;
		font-weight: 400;
		font-size: 16px;
		line-height: 24px;
		letter-spacing: 0%;
		text-align: center;
		vertical-align: bottom;
		bottom: 7px;
		margin-left: 14px;
	}
  .new-project-icon {
		margin-top: 5px;
		width: calc(var(--spacing) * 6);
  	height: calc(var(--spacing) * 6);
  }
  .rigth-side {
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    margin-top: 15px;
  }
  .custom-select {
    width: 296px;
    height: 40px;
    border-radius: 8px;
    border-width: 1px;
    background-color: white;
    border-color: #717171;
    padding: 0 10px;
    font-size: 14px;
    color: #333;
    margin-inline: 20px;
  }
  .favorites-text {
    color: #1E1E1E;
    font-family: Encode Sans Semi Expanded;
    font-weight: 400;
    font-size: 16px;
    line-height: 22px;
    letter-spacing: 0%;
    margin-left: 10px;
  }
</style>