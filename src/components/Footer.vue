<template>
	<section class="container">
		<footer class="container__footer">
			<span class="container__header-motto">{{ motto }}</span>
		</footer>
	</section>
</template>

<script>
	export default {
		data() {
			return {
				motto: '@CartaDesign'
			}
		}
	}
</script>

<style scoped>
	.container {
		display: grid;
		grid-template-columns: var(--grid-column-12);
		grid-auto-rows: minmax(100px, auto);
		
	}

	.container__footer {
		display: grid;
		grid-column: 1/ span 12;
		background-color: #80a08a; 
		height: 100px;
	}

	.container__header-motto {
		grid-column: 1/ span 3;
		font-size: 2rem;
		color: rgb(56, 9, 13);
		grid-row: 1;
		padding-top: 10px;
		padding-left: 10px;
		font-family: cursive;
	}


</style>