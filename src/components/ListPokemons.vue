<script setup>

const pokemon = defineProps(["name", "urlBaseSvg"]);

</script>

<template>
    <div class="col-4 mb-3">
        <div class="card text-center p-3 cardListPokemon">
            <p>{{ pokemon.name }}</p>
            <img :src="urlBaseSvg" 
            class="card-img-top" 
            alt="..."
            height="200">
        </div>
    </div>
</template>
    
<style scoped>

.cardListPokemon{
    background: rgb(83,78,135);
    background: radial-gradient(circle, rgba(83,78,135,0.7456232492997199) 0%, rgba(148,187,233,0.6027661064425771) 100%);
    cursor: pointer;
}
.cardListPokemon:hover{
    background: rgb(83,78,135);
    background: radial-gradient(circle, rgba(83,78,135,0.9) 0%, rgba(148,187,233,0.8) 100%);
}
.cardListPokemon img:hover{
    padding: .2rem;
}

</style>