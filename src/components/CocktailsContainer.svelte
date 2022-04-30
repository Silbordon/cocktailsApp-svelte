<script lang="ts">
    import axios from "axios";
    import Cocktail from "./Cocktail.svelte";
import ErrorCocktails from "./ErrorCocktails.svelte";
    import Loading from "./Loading.svelte";

    let drinks: Array<any> = [];
    let drinkName: string = "";

    const getDrinks = async (drinkName: string = "margarita") => {

        if(drinkName.trim()=== ""){
            throw new Error("this field es requerired")
        }


        const { data } = await axios.get(
            `https://www.thecocktaildb.com/api/json/v1/1/search.php?s=${drinkName}`
        );
        drinks = data.drinks;
        return drinks
    };

    let promise = getDrinks();

    const handlerSubmit = () => {
        promise = getDrinks(drinkName);
    };
</script>

<div class="container text-center mt-3">
    <h2>Search Cocktails</h2>

    <form on:submit|preventDefault={handlerSubmit} class="d-flex container-form">
        <input bind:value={drinkName} type="text" class="form-control mx-2" />
        <button type="submit" class="btn btn-warning">Seach</button>
    </form>

    {#await promise}
        <Loading />
    {:then drinksResponde}
        <div class="row container-cocktails">
            {#each drinks as drink}
                <Cocktail drinkData={drink} />
            {/each}
        </div>
    {:catch err}
        <ErrorCocktails {err}/>
    {/await}
</div>

<style>
   
    .container {
        width: 80%;
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;
    }
    .container-form{
        width: 80%;
        margin-top: 20px;
    }
    input {
        border-radius: 10px;
    }
    button{
        border-radius: 10px;
    }
    .container-cocktails {
        width: 100%;
        margin-top: 30px;
        display: flex;
        justify-content: center;
        flex-wrap: wrap;
    }
</style>
