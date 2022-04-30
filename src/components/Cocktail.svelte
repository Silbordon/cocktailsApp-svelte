
<script lang="ts">
        import {fade} from "svelte/transition";

    export let drinkData: any;
</script>


<div transition:fade class="card m-3 b-radius" style="width: 18rem;">
    <img 
        loading="lazy"
        src={drinkData.strDrinkThumb} 
        class="card-img-top pt-2 b-radius" 
        alt={drinkData.idDrink}>
    <div class="card-body">
      <h5 class="card-title">{drinkData.strDrink}</h5>
      <p class="card-text">{drinkData.strInstructions}</p>
    </div>
  </div>

  <style>
      .b-radius{
        border-radius: 10px;
      }
  
  </style>