<script setup>

import { computed } from 'vue';

const pokemon = defineProps(["name","height","xp","img", "loading"])
// const uppercaseName = computed(()=> pokemon.name.toUpperCase());

</script>

<template>
    <div class="card cardSelecedPokemon" :class="loading ? '' : 'animate__animated animate__flipInY'">
        <img v-if="pokemon.name" :src="pokemon.img" class="card-img-top pt-2" :alt="pokemon.name" height="250">
        <img v-else src="../assets/egg_pokemon.svg" class="card-img-top pt-2" alt="???" height="250">
        <div class="card-body">
            <h5 class="card-title text-center">{{ pokemon.name || "???" }}</h5>
            <hr>
            <div class="row">
                <section class="col">
                    <strong>XP: </strong>
                    <span>{{ pokemon.xp }}</span>
                </section>
                <section class="col">
                    <strong>Altura: </strong>
                    <span>{{ pokemon.height }}</span>
                </section>
            </div>
        </div>
    </div>
</template>

<style scoped>

.cardSelecedPokemon{
    height: 80vh;
    background-color: #ffaf3c;
    background-image: linear-gradient(225deg, #ffaf3c 0%, #a0894b 50%, #c5802b 100%);

    /* background: rgb(131,58,180);
    background: radial-gradient(circle, rgba(131,58,180,0.7288165266106443) 0%, rgba(252,176,69,0.7232142857142857) 95%); */
}

</style>