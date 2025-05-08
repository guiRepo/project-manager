<script setup lang="ts">
	import { ref } from 'vue'

	const form = ref({
		nome: '',
		cliente: '',
		inicio: '',
		fim: '',
		capa: null,
		capaPreview: null
	})

	const handleFile = (e) => {
		const file = e.target.files[0]
		if (file) {
			form.value.capa = file
			form.value.capaPreview = URL.createObjectURL(file)
		}
	}

	const handleSubmit = () => {
		console.log('Formulário enviado:', form.value)
		// Aqui você pode enviar via fetch ou $fetch para uma API
	}
</script>

<template>
	<main class="container">
		<div class="container-return">
			<UIcon name="i-lucide-arrow-left" class="icon" />
			<h2 class="text-return">Voltar</h2>
		</div>
		<h1 class="new-project-title">Novo Projeto</h1>

	<section >
		<div class="container-itens">
			<form  @submit.prevent="handleSubmit">
				<div>
					<label class="text-input">Nome do projeto <span class="required">(Obrigatório)</span></label>
					<input v-model="form.nome" required class="w-196 p-2 border rounded focus:outline-none focus:ring focus:ring-purple-400 text-black bg-white" type="text" />
				</div>

				<div>
					<label class="text-input">Cliente <span class="required">(Obrigatório)</span></label>
					<input v-model="form.cliente" required class="w-196 p-2 border rounded focus:outline-none focus:ring focus:ring-purple-400 text-black bg-white" type="text" />
				</div>

				<div class="flex space-x-4">
					<div class="flex-1">
						<label class="text-input">Data de Início <span class="required">(Obrigatório)</span></label>
						<input v-model="form.inicio" required class="w-full p-2 border rounded focus:outline-none focus:ring focus:ring-purple-400  text-black bg-white" type="date" />
					</div>
					<div class="flex-1">
						<label class="text-input">Data Final <span class="required">(Obrigatório)</span></label>
						<input v-model="form.fim" required class="w-full p-2 border rounded focus:outline-none focus:ring focus:ring-purple-400  text-black bg-white" type="date" />
					</div>
    		</div>
				<div>
					<label class="text-input">Capa do projeto</label>
					<div class="border-dashed border-2 border-gray-600 p-4 rounded text-center">
						<input type="file" accept="image/png, image/jpeg" class="hidden" ref="fileInput" @change="handleFile" />
						<div @click="$refs.fileInput.click()" class="cursor-pointer inline-block px-4 py-2 mt-2 text-gray-600 border border-gray-600 rounded hover:bg-purple-100">
							Selecionar
						</div>
						<div v-if="form.capaPreview" class="mt-4">
							<img :src="form.capaPreview" class="max-h-40 mx-auto rounded" />
						</div>
					</div>
				</div>


				<button type="submit" class="w-full py-3 bg-purple-400 text-white rounded-full hover:bg-purple-500 transition">
					Salvar projeto
				</button>
			</form>

			<!-- <div class="container-input">
				<label class="text-input">Nome do projeto <span class="required">(Obrigatório)</span></label>
				<input class="input-name" type="text">
			</div>
			<div class="container-input">
				<label class="text-input">Cliente <span class="required">(Obrigatório)</span></label>
				<input class="input-name" type="text">
			</div>

			<div class="container-data">
				<div class="container-input">
					<label class="text-input">Nome do projeto <span class="required">(Obrigatório)</span></label>
					<input class="input-data" type="text">
				</div>
				<div class="container-input">
					<label class="text-input">Nome do projeto <span class="required">(Obrigatório)</span></label>
					<input class="input-data" type="text">
				</div>
			</div>

			<div class="container-input">
				<label class="text-input">Cliente <span class="required">(Obrigatório)</span></label>
				<button>
					<input class="input-name" type="file">
				</button>
			</div> -->
		</div>
	</section>
	</main>
</template>

<style scoped>
	.container-return {
		display: flex;
		flex-direction: row;
	}
	.text-return {
		color: #695CCD;
		font-family: Encode Sans Semi Expanded;
		font-weight: 400;
		font-size: 16px;
		line-height: 100%;
		letter-spacing: 0%;
		vertical-align: middle;
	}
	.icon {
		color: #695CCD;
	}
	.new-project-title {
		color: #1F1283;
		font-family: Encode Sans Semi Expanded;
		font-weight: 600;
		font-size: 24px;
		line-height: 100%;
		letter-spacing: 0%;
		vertical-align: middle;
	}
	.item-form {
		display: flex;
		flex-direction: column;
	}
	.required {
		color: #717171;
		font-family: Encode Sans Semi Expanded;
		font-weight: 400;
		font-size: 14px;
		line-height: 22px;
		letter-spacing: 0%;
		vertical-align: bottom;
	}
	.title-item {
		color: #695CCD;
		font-family: Encode Sans Semi Expanded;
		font-weight: 500;
		font-size: 18px;
		line-height: 22px;
		letter-spacing: 0%;
		vertical-align: bottom;
	}
	.container-itens {
		margin: 1.5rem auto; 
		width: 100%;            
		height: 683px;
		max-width: 100%; 
		border-width:  1px;
		border-color: #DCDCDC;
		border-radius: 8px;
		box-sizing: border-box;
		
		display: flex;
		align-items: center;
		justify-content: center;
		flex-direction: column;
	}
	.container {

		max-width: 100%; 

	}

	.container-data {
		display: flex;
		flex-direction: row;
	}
	.input-data {
		border-color: #717171;
		width: 332px;
		height: 40px;
		top: 522px;
		left: 990px;
		border-radius: 4px;
		border-width: 1px;
	}

	.container-input {
		display: flex;
		flex-direction: column;
	}
	.input-name {
		width: 702px;
		height: 40px;
		top: 299px;
		left: 620px;
		border-radius: 8px;
		border-width: 1px;
		border-color: #717171;
		color: #695CCD;
	}
	.text-input {
		display: block;
		color: #695CCD;
		font-family: Encode Sans Semi Expanded;
		font-weight: 500;
		font-size: 18px;
		line-height: 22px;
		letter-spacing: 0%;
		margin-bottom: calc(var(--spacing) * 1) 
	}
</style>
