<script setup>
import { onMounted, reactive, ref, computed } from 'vue';
import ListPokemons from '@/components/ListPokemons.vue';
import CardPokemonSelected from '@/components/CardPokemonSelected.vue';

const pokemons = reactive([]);
const urlBaseSvg = ref("https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/");
const searchPokemonField = ref("");
let pokemonSelected = reactive(ref());
let loading = ref(false)
onMounted(() => {
  fetch("https://pokeapi.co/api/v2/pokemon?limit=400&offset=0")
    .then(res => res.json())
    .then(res => pokemons.push(...res.results));
});

const pokemonsFiltered = computed(() => {
  if (pokemons.length && searchPokemonField.value) {
    return pokemons.filter(pokemon =>
      pokemon.name.toLowerCase().includes(searchPokemonField.value.toLowerCase())
    );
  }
  return pokemons;
});

const selectPokemon = async (pokemon) => {
    loading.value = true;
    try {
        const response = await fetch(pokemon.url);
        if (!response.ok) {
            throw new Error(`HTTP error! status: ${response.status}`);
        }
        const data = await response.json();
        pokemonSelected.value = data;
        console.log(pokemonSelected.value);
    } catch (error) {
        console.error('Error fetching Pokémon data:', error);
    } finally {
        loading.value = false;
    }
};

</script>

<template>
    <div class="container">
        <div class="row mt-4">
            <div class="col-sm-12 col-md-6">
                <CardPokemonSelected
                    :name = "pokemonSelected?.name"
                    :xp="pokemonSelected?.base_experience"
                    :height="pokemonSelected?.height"
                    :img = "pokemonSelected?.sprites.other.dream_world.front_default"
                    :loading ="loading"
                />
            </div>
            <div class="col-sm-12 col-md-6">
                <div class="card card-list">
                    <div class="card-body row">

                        <div class="mb-3">
                            <label hidden for="searchPokemonField" class="form-label">Pesquisar...</label>
                            
                            <input type="text" class="form-control" id="searchPokemonField"
                                placeholder="Pesquisar..."
                                v-model = "searchPokemonField"
                                >
                        </div>

                        <ListPokemons v-for="pokemon in pokemonsFiltered" :key="pokemon.name" :nome="pokemon.name"
                            :urlImagemSvg="urlBaseSvg + pokemon.url.split('/')[6] + '.svg'" 
                            @click="selectPokemon(pokemon)"
                            />
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped>
.card-list{
    max-height: 75vh;
    overflow-y: scroll;
    overflow-x: hidden;
}
</style>
