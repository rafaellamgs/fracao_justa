<script lang="ts">
    import Users from  './Users.svelte';
</script>

<main>
    <h1>Escalonamento por Fração Justa</h1>
    <Users    />
</main>







<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>