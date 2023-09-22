<script setup>
import Header from './components/Header.vue';
import Search from './components/Search.vue';
import Footer from './components/Footer.vue';
import { ref, onBeforeMount, } from 'vue';
const allPokemons = ref([]);

onBeforeMount(()=>{
  fetch('https://pokebuildapi.fr/api/v1/pokemon/')
  .then((res)=> res.json())
  .then(data => {
    allPokemons.value = data;
    console.log(allPokemons.value);
  })
})
</script>

<template>    
 
 <section>
      <Header />
      <main>
       <Search :pokemonList = "allPokemons" />
      </main>
      <Footer />      
    </section>
</template>

<style>

* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;  
}

section {
    color: rgb(40, 228, 253);
    width: 100vw;
    height: 100vh;
    background: url(../src/assets/images/background-image.jpg);
    background-size: 100% 100%; 
    background-size: cover;
    background-repeat: no-repeat;
}

header {
    text-align: center; 
    padding: 60px;  
    display: flex;
    flex-direction: row;
    justify-content: space-between;

}

#pokem {
    width: 10vw;
}

#poke {
    max-width: 70%;
}

h1 {
    font-family: Verdana, Geneva, Tahoma, sans-serif;
    padding: 10px 50px;
    width: 60%;
}

.boutton > button {
   padding: 15px 15px;
}

main {
    display: flex;
    flex-direction: column;
}

form {
    width: 50%;
    margin: auto;
}

#accueil {
    display: flex;
    justify-content: center;
}

fieldset {
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 30vw;
    height: 20vh;
    background-color: azure;
    padding: 10px;
    margin: auto;
    border-radius: 15px;
    border: 1px solid azure;
}

legend {
  color: rgb(40, 228, 253);
  background-color: azure;
  border-radius: 5px;
  padding: 5px 10px;

}

article {
    display: flex;
    flex-direction: column;
    align-items: center;
    color: rgb(4, 84, 153);
    font-size: 1.5rem;
    margin-top: 20px;
}

#image {
    max-width: 30%;
}

select {
    width: 40%;
    margin: 20px;
    border-radius: 5px;
    
}

select:hover {
    background-color: azure;
}

p {
    background-color: rgba(65, 208, 160, 0.314);
    color: rgb(3, 3, 123);
    padding: 5px 10px;
    margin: 2px;
    border-radius: 6px;
}

input[type=submit] {
    padding: 5px 10px;
    border-radius: 8px;
}

input[type=submit]:hover {
    background-color: rgb(110, 228, 228);
}

button {
    padding: 5px 10px;
    border-radius: 8px;
    background-color: rgb(201, 210, 210);
}

button:hover {
    background-color: rgb(110, 228, 228);
}

a {
    text-decoration: none;
}

footer {
  position: absolute;
  display: flex;
  justify-content: flex-end;
  bottom: 0;
 width: 100vw;
}
</style>
