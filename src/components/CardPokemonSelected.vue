<script setup>
const pokemon = defineProps(["name", "xp", "height","img", "loading"])
</script>

<template>
    <div class="card CardList"
        
    >
        <img 
        v-if="pokemon.name"
        :src="pokemon.img" class="card-img-top pt-2"
        :class="loading ? '' : 'animate__animated animate__zoomIn'"
            alt="pokemon.name"
            height="250"
            
            
        >
        <img 
        v-else
        src="../assets/pokebola.svg" class="card-img-top pt-2"
        :class="loading ? '' : 'animate__animated animate__zoomIn'"
            alt="???"
            height="250"
        >
        <div class="card-body">
            <h5 class="card-title text-center">{{ pokemon.name  || '???'}}</h5>
            <hr>
            <div class="row">
                <selection class="col">
                    <strong>XP: </strong>
                    <span> {{ pokemon.xp }}</span>
                </selection>
                <selection class="col">
                    <strong>Altura: </strong>
                    <span> {{ pokemon.height }}</span>
                </selection>
            </div>
        </div>
    </div>
</template>

<style scoped>
.CardList{
    height: 75vh;
    background: rgb(241,251,63);
    background: radial-gradient(circle, rgba(150, 76, 11, 0.512) 0%, rgba(252, 70, 70, 0.585) 100%);
}
</style>