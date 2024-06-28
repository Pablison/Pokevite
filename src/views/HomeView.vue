<script setup>
import { onMounted, reactive, ref, computed } from 'vue';
import ListPokemons from "../components/ListPokemons.vue"
import CardPokemonSelected from "../components/CadPokemonSelected.vue"

let pokemons = reactive(ref());
let urlBaseSvg = ref("https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/");
let searchPokemon = ref("")
let pokemonSelected = reactive(ref())
let loading = ref(false)

onMounted(() => {
  fetch("https://pokeapi.co/api/v2/pokemon?limit=151&offset=0")
    .then(res => res.json())
    .then(res => pokemons.value = res.results);
})

const pokemonsFiltered = computed(() => {
  if (pokemons.value && searchPokemon.value) {
    return pokemons.value.filter(pokemon =>
      pokemon.name.toLowerCase().includes(searchPokemon.value.toLowerCase())
    )
  }
  return pokemons.value;
})

const selectedPokemon = async (pokemon) => {
  loading.value = true;
  await fetch(pokemon.url)
  .then(res => res.json())
  .then(res=> pokemonSelected.value = res)
  .catch(err => alert(err))
  .finally(()=> loading.value = false)
console.log(loading.value);
}

</script>

<template>
  <main>

    <div class="container-fluid">
      <div class="row mt-4">      
        <div class="col-sm-12 col-md-6">
          <div class="card card-list">
            <div class="card-body row">
              <div class="mb-3">
                <label hidden for="searchPokemon" class="form-label">Pesquisar...</label>
                <input v-model="searchPokemon" type="text" class="form-control" id="searchPokemon"
                placeholder="Pesquisar...">
              </div>
              
              <ListPokemons v-for="pokemon in pokemonsFiltered" :key="pokemon.name" :name="pokemon.name" @click="selectedPokemon(pokemon)"
              :urlBaseSvg="urlBaseSvg + pokemon.url.split('/')[6] + '.svg'" />
            </div>
          </div>
        </div>

        <div class="col-sm-12 col-md-6">
          <CardPokemonSelected 
            :name="pokemonSelected?.name"
            :height="pokemonSelected?.height"
            :xp="pokemonSelected?.base_experience"
            :img="pokemonSelected?.sprites.other.dream_world.front_default"
            :loading="loading"
          />
        </div>
        
      </div>
    </div>
  </main>
</template>

<style scoped>

.card-list{
  max-height: 80vh;
  overflow-y: scroll;
  overflow-x: hidden;
}

</style>