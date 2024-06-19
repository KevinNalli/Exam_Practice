<script setup>
import { ref } from 'vue';


const name = ref('');
const phrase = ref('');
const image = ref('');
const dire = ref('');


async function call() {
  try {
    const response = await fetch('https://thesimpsonsquoteapi.glitch.me/quotes?count=1');
    const data = await response.json();
    asignacion(data);
  } catch (error) {
    console.error('Error en la solicitud:', error);
  }
}


function asignacion(data) {
  name.value = data[0].character;
  phrase.value = data[0].quote;
  image.value = data[0].image;
  dire.value = data[0].characterDirection;
}


call();
</script>

<template>
    <div class="rounded-xl shadow-xl p-5 w-[450px] h-auto">
        <div class="flex justify-center items-center gap-4">
            <div class="w-full">
                <img :src=image alt="" class="rounded-full size-36 shadow">
            </div>
            <div>
                <h1 class="font-semibold">Nombre = {{name}}</h1>
                <span class="font-semibold" >Frase</span>
                <span class="font-semibold w-56" >{{phrase}}</span>
            </div>
        </div>
    </div>
</template>