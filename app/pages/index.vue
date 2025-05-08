<script setup>
</script>


<template>
	<div class="container">	
		<h1 class="title">Nenhum projeto</h1>
		<h3 class="sub-title">Clique no botão abaixo para criar o primeiro e gerenciá-lo.</h3>
		<NuxtLink to="/projects/new" class="new-project">
			<button class="new-project-button">
				<UIcon name="i-lucide-circle-plus" class="icon" />
			<label class="new-project-button-text">Novo projeto</label>
		</button>
		</NuxtLink>
	</div>
</template>

<style scoped>
	.container {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		max-width: 100%; 
		background-color: #ffff;
	}
	.new-project-button {
		background-color: #695CCD;
		width: 230px;
		height: 52px;
		border-radius: 26px;
		margin-top: 20px
	}
	.new-project-button-text {
		position: relative;
		font-family: Encode Sans Semi Expanded;
		font-weight: 400;
		font-size: 20px;
		line-height: 22px;
		letter-spacing: 0%;
		text-align: center;
		vertical-align: bottom;
		bottom: 7px;
		margin-left: 14px;

	}
	.title {
		color: #1F1283;
		font-family: Encode Sans Semi Expanded;
		font-weight: 600;
		font-size: 24px;
		line-height: 100%;
		letter-spacing: 0%;
		text-align: center;
		vertical-align: middle;
		margin-bottom: 20px;
	}
	.sub-title {
		color: #717171;
		font-family: Encode Sans Semi Expanded;
		font-weight: 400;
		font-size: 16px;
		line-height: 22px;
		letter-spacing: 0%;
		text-align: center;
		margin-block: 10px;
	}

	.icon {
		margin-top: 5px;          /* Ajuste da distância entre o ícone e o texto */
		width: calc(var(--spacing) * 6) /* 1.5rem = 24px */;
  	height: calc(var(--spacing) * 6) /* 1.5rem = 24px */;
	}
</style>