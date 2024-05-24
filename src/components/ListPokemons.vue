<script setup>
const props = defineProps(["nome", "urlImagemSvg"])
</script>

<template>
  <div class="col-4">
    <div class="card  p-2 mb-3 cardListPokemon">
      <p class="text-center">{{ nome }}</p>
      <img :src="urlImagemSvg" 
      class="card-img-top" 
      alt="Imagem do Pokémon"
      height="85"
      />
    </div>
  </div>
</template>

<style scoped>
.cardListPokemon{
    background: rgb(241,251,63);
    background: radial-gradient(circle, rgba(241,251,63,0.5116248381765265) 0%, rgba(252,172,70,0.5847242533812049) 100%);
    cursor: pointer;
}
.cardListPokemon:hover{
    background: rgb(241,251,63);
    background: radial-gradient(circle, rgba(241,251,63,0.695835364492316) 0%, rgba(252,172,70,0.8069464756034271) 100%);
}
.cardListPokemon img:hover{
    padding: .1rem;
}
</style>
