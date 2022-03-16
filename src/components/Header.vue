<template>
	<section class="container">
		<header class="container__header">
			<img class="container__header__logo" src="/images/logo.png" alt="app-logo">

	</header>
	</section>
</template>

<script>
export default {
	data() {
		return {

		}
	},
	
}
</script>

<style scoped>
	.container {
		display: grid;
		grid-template-columns: var(--grid-column-12);
		grid-auto-rows: minmax(100px, auto);
		
	}

	.container__header {
		box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
		background-color: #a8ceb4; 
		grid-column: 1/ span 12;
		display: grid;
		height: 210px;
		/* padding-top: 10px; */
		margin-bottom: 10px;
	}

	.container__header__logo {
		transition: transform 1s ease-in-out;
		width: 20%;
		padding: 0px 0px 0px 0px;
		grid-column: 1/ span 4;
		grid-row: 1;
	}

	.container__header__logo:hover {
		transform: rotateZ(360deg);
	}
   
	/* small and medium devices */
	@media screen and (max-width: 1024px) {
		.container__header__logo {
			width: 25%;
		}
	}

</style>