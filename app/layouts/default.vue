<template>
	<div>
		<nav class="navBar">
      <NuxtLink to="/" class="logo">
        <img src="~assets/images/logo.png" alt="Ir para Home"   loading="lazy">
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
  z-index: 5;
}
</style>