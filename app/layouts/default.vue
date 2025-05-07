<template>
	<div>
		<nav class="navBar">
			<img src="~assets/images/logo.svg">
            
		</nav>
		<main class="container">
			<slot />
		</main>
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
</style>
