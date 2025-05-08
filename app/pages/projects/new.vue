<script setup lang="ts">
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
			<div class="container-input">
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
			</div>
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
		color: #695CCD;
		font-family: Encode Sans Semi Expanded;
		font-weight: 500;
		font-size: 18px;
		line-height: 22px;
		letter-spacing: 0%;
		vertical-align: bottom;

	}
	.required {
		columns: #717171;
		font-family: Encode Sans Semi Expanded;
		font-weight: 400;
		font-size: 14px;
		line-height: 22px;
		letter-spacing: 0%;
		vertical-align: bottom;
	}


</style>
