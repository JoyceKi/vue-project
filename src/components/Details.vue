<script setup>
const props = defineProps({
    pokemonDetails: Object
})
</script>
<template>   
    <!-- v-bind permet d'afficher l'image correctement (pas juste l'url de l'image)
    .map permet d'examiner l'objet comme si c'était un tableau, .join a la même fonction que implode et on y met un séparateur (,  )
    v-if permet d'afficher ou pas l'évolution -->
    <article id="infos">  
        <h2>{{ pokemonDetails.name }}</h2>
        <img id="image" v-bind:src="pokemonDetails.image" alt="{{ pokemonDetails.name }}">
        <p id="types" >Élément : {{ pokemonDetails.apiTypes.map((type)=> type.name).join(", ") }}</p>
        <p id="evolution" v-if="pokemonDetails.apiEvolutions[0] !== undefined">
            Évolution : {{ pokemonDetails.apiEvolutions.map((evol)=> evol.name).join(", ") }}             
        </p>
                       
    </article>            
               
    <article id="stats">  
        <ul class="stats">
            <!-- Une boucle for pour lister tous les éléments de l'objet pokemonDetails.stats-->
            <!-- <li v-for="(value, property) in pokemonDetails.stats">
                {{ property.toUpperCase() }} :  {{ value }}
            </li> -->
            <!-- Une autre façon de faire : remplir la liste une à une -->
            <li > HP  : {{ pokemonDetails.stats.HP }}</li>
            <li > Attaque : {{ pokemonDetails.stats.attack }}</li>
            <li > Défense : {{ pokemonDetails.stats.defense }}</li>
            <li > Attaque spéciale : {{ pokemonDetails.stats.special_attack }}</li>
            <li > Défense spéciale : {{ pokemonDetails.stats.special_defense }}</li>
            <li > Vitesse  : {{ pokemonDetails.stats.speed }}</li>
                            
        </ul>                        
    </article>

</template>