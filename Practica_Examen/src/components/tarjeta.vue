<script setup>
    import { ref } from 'vue';
    
    let image = ref('')
    let character = ref('')
    let direccion = ref('')
    let quote = ref('')


    async function call(){
        try{
            const response = await (await fetch('https://thesimpsonsquoteapi.glitch.me/quotes?count=num')).json()
            await asignacion(response);
        }catch(error){
            console.log("Error en la peticion ", error);
        }
    }
    function asignacion(url){
        image.value = url[0].image
        character.value = url[0].character
        direccion.value = url[0].characterDirection
        quote.value = url[0].quote
    }
    call();





</script>
<template>
    <div class="mt-4 shadow-2xl p-8 flex max-h-64 max-w-[700px] rounded-xl select-none">
        <div v-if="direccion=='Left'" class="w-1/3 flex items-center justify-center rounded-full drop-shadow-2xl">
            <img :src=image alt="XD" class=" h-48" >
        </div>
        <div class="w-2/3 p-4">
            <h1 class="font-semibold">Nombre: <h1 class="font-normal">{{ character }}</h1></h1>
            <h2 class="font-semibold">Frase:</h2>
            <h2 class="font-normal">{{ quote }}</h2>
        </div>
        <div v-if="direccion=='Right'" class="w-1/3 flex items-center justify-center rounded-full ">
            <img :src=image alt="XD" class=" h-48" >
        </div>
    </div>
</template>