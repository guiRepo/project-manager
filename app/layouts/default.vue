<template>
	<div>
		<nav class="navBar">
			<img src="~assets/images/logo.svg">
            
		</nav>
		<div class="container">
			<slot />
		</div>
	</div>
</template>

<style scoped>
.navBar {
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  background-color: #1C1930;
  width: 100%;
  height: 80px;
}

.container {
  

  margin: 1.5rem auto;         /* margem vertical e centralização horizontal */
  width: 95%;             /* largura relativa à tela */
  height: 100%;
  max-width: 100%;          /* evita esticar demais em telas grandes */

  background-color: brown;
  border-radius: 4px;
  box-sizing: border-box;    /* padding incluído no cálculo do tamanho */
}
</style>
