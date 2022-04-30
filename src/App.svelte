<script lang="ts">
import CocktailsContainer from "./components/CocktailsContainer.svelte";
import NavBar from "./components/NavBar.svelte";


</script>

<main>
	<NavBar />
	<CocktailsContainer/>
</main>

<style>
	main{
		background-color: rgba(126, 109, 109, 0.301);
		height: 100%;
		padding: 20px;
	}
</style>