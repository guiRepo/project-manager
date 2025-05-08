<template>
	<div>
		<nav class="navBar">
      <NuxtLink to="/" class="logo">
        <img src="~assets/images/logo.svg" alt="Ir para Home">
      </NuxtLink>
            
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
  display: flex;
  margin: 3.5rem auto; 
  width: 95%;            
  height: 880px;
  max-width: 100%; 
  border-width:  1px;
  border-color: black;
  border-radius: 4px  black;
  box-sizing: border-box; 
}
.logo img {
  width: 193px;
  height: 72px;
  cursor: pointer;
  transition: transform 0.2s ease;
}
.logo img:hover {
  transform: scale(1.05);
}
</style>