<script setup>
import { ref } from 'vue'
import Details from './Details.vue'
const pokemonSelected = ref("");
const props = defineProps({
    pokemonList : Array
})
const isPokemon = ref(false)
const pokemonDatas = ref({})

function afficherDetails() {
    console.log("cliqué")
    fetch('https://pokebuildapi.fr/api/v1/pokemon/' + pokemonSelected.value)
    .then((res)=> res.json())
    .then(carac => {
        console.log("Détails :",carac);
        pokemonDatas.value = carac
        isPokemon.value = true
})
}
</script>
<template>
     <form action="" name="form">
                <fieldset>
                    <legend>
                        <strong> Sélectionnez un Pokémon</strong>
                    </legend>   
                    <select id="choisir" name="choisir" v-model="pokemonSelected"> 
                      <option v-for="myPokemon in pokemonList" :value="myPokemon.id" >
                          {{ myPokemon.name }}
                      </option>
                    </select>  
                    <input @click="afficherDetails" @click.prevent="" type="submit" value="Choisir">          
                </fieldset>  
                <Details v-if="isPokemon" :pokemonDetails="pokemonDatas"/>         
            </form>   
</template>