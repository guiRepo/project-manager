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
		<div>
			<NuxtLink to="/" class="container-return">
				<UIcon name="i-lucide-arrow-left" class="icon" />
				<h2 class="text-return">Voltar</h2>
			</NuxtLink>
		</div>
		<h1 class="new-project-title">Novo Projeto</h1>

	<section>
		<div class="container-itens">
			<form  @submit.prevent="handleSubmit">
				<div class="container-input">
					<label class="text-input">Nome do projeto <span class="required">(Obrigatório)</span></label>
					<input v-model="form.nome" required class="w-196 p-2 border rounded focus:outline-none focus:ring focus:ring-purple-400 text-black bg-white" type="text" >
				</div>

				<div class="container-input">
					<label class="text-input">Cliente <span class="required">(Obrigatório)</span></label>
					<input v-model="form.cliente" required class="w-196 p-2 border rounded focus:outline-none focus:ring focus:ring-purple-400 text-black bg-white" type="text" >
				</div>

				<div class="flex space-x-4">
					<div class="flex-1">
						<label class="text-input">Data de Início <span class="required">(Obrigatório)</span></label>
						<input v-model="form.inicio" required class="w-full p-2 border rounded focus:outline-none focus:ring focus:ring-purple-400  text-black bg-white accent-purple-500"  type="date">
					</div>
					<div class="flex-1">
						<label class="text-input">Data Final <span class="required">(Obrigatório)</span></label>
						<input v-model="form.fim" required class="w-full p-2 border rounded focus:outline-none focus:ring focus:ring-purple-400  text-black bg-white" type="date" >
					</div>
    		</div>

				<div class="cover-container">
					<label class="text-input">Capa do projeto</label>
					<div class="file-container">
						<UIcon name="i-lucide-hard-drive-upload" class="icon" />
						<label class="required">Escolha uma imagem .jpg ou .png no seu dispositivo</label>
							<input ref="fileInput"  type="file" accept="image/png, image/jpeg" class="hidden" @change="handleFile" >
							<div class="file-button" @click="$refs.fileInput.click()">Selecionar</div>
							<div v-if="form.capaPreview" class="mt-4">
									<img :src="form.capaPreview" class="max-h-40 mx-auto rounded" >
							</div>
					</div>
				</div>

				<button type="submit" class="salve-file">
					Salvar projeto
				</button>
			</form>
		</div>
	</section>
	</main>
</template>

<style scoped>
	.file-container {
		padding: 30px;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		border-style: dashed;
		border-width: 1px;
		border-color: #717171;
		border-radius: 4px;	
		text-align: center;
	}
	.container-return {
		display: flex;
		flex-direction: row;
	}
	.text-return {
		display: flex;
		color: #695CCD;
		font-family: Encode Sans Semi Expanded;
		font-weight: 400;
		font-size: 19px;
		line-height: 100%;
		letter-spacing: 0%;
		vertical-align: middle;
		margin-top: 3px;
		margin-left: 10px;
	}
	.icon {
		color: #695CCD;
		width: calc(var(--spacing) * 6) /* 1.5rem = 24px */;
  	height: calc(var(--spacing) * 6) /* 1.5rem = 24px */;
	}
	.new-project-title {
		color: #1F1283;
		font-family: Encode Sans Semi Expanded;
		font-weight: 600;
		font-size: 24px;
		line-height: 100%;
		letter-spacing: 0%;
		vertical-align: middle;
		margin-top: 15px;
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
		border-style: dashed;
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
		margin-bottom: 30px;
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
	.file-button {
		width: 144px;
		cursor: pointer;
		display: flex;
		justify-content: center;
		align-items: center;

		padding-inline: calc(var(--spacing)*4);
		padding-block: calc(var(--spacing)*2);
		margin-top: calc(var(--spacing)*2);
		
		color: #695CCD;
		border-style: var(--tw-border-style);
		border-width: 1px;
		border-color: #695CCD;
		border-radius: 45px;
	}
	.cover-container {
		display: flex;
		flex-direction: column;
		margin-top: 30px;
	}
	.salve-file {
		width: 100%;
		padding-block: calc(var(--spacing)*3);
		background-color: #B2A8FF;
		color: white;
		border-radius: calc(infinity * 1px);
		margin-top: 30px;
	}
</style>