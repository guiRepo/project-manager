<script setup lang="ts">
import CardProject from '~/components/CardProject.vue';

const allProjects = ref([]);
const value = ref(true);
const filtroSelecionado = ref('alphabetical');
const filtros = [
  { label: 'Orden alfabética', value: 'alphabetical' },
  { label: 'Mais recentes', value: 'recent' },
  { label: 'Prazo mais próximo', value: 'deadline' }
]

const projetosOrdenados = computed(() => {
  const lista = [...allProjects.value]
  switch (filtroSelecionado.value) {
    case 'alphabetical':
      return lista.sort((a, b) => a.projectName.localeCompare(b.projectName))
    case 'recent':
      return lista.sort((a, b) => new Date(b.beginDate).getTime() - new Date(a.beginDate).getTime())
    case 'deadline':
      return lista.sort((a, b) => new Date(a.endDate).getTime() - new Date(b.endDate).getTime())
    default:
      return lista
  }
});

onMounted(() => {  
  const projetosSalvos = localStorage.getItem('allProjects')
  if (projetosSalvos) {
    allProjects.value = JSON.parse(projetosSalvos)
  }

  const dados = localStorage.getItem('novoProjeto')
  
  if (dados) {
    console.log(dados);
    
    allProjects.value.push(JSON.parse(dados))
    localStorage.removeItem('novoProjeto')
  }
})

watch(allProjects, (novaLista) => {
  localStorage.setItem('allProjects', JSON.stringify(novaLista))
}, { deep: true })
</script>

<template>
  <main class="container px-4 md:px-8">
    <div class="header">
      <div class="left-side">
        <h1 class="list-project-title">Projeto  <span class="number-projects">({{ projetosOrdenados.length }})</span></h1>
      </div>

      <div class="rigth-side">
        <USwitch v-model="value" />
        <span class="favorites-text"> Apenas favoritos</span>
        <select v-model="filtroSelecionado" class="custom-select">
          <option v-for="filtro in filtros" :key="filtro.value" :value="filtro.value">
            {{ filtro.label }}
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
        v-for="(projeto, index) in projetosOrdenados"
        :key="index"
        :project-id="projeto.projectId"
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