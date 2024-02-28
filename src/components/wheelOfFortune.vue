<template>
    <div class="container">
        <div class="wheel-container">
            <img class='arrow' :src="arrow" alt="Стрелочка">
            <img class="wheel" :src="wheelImage" :style="{ transform: `rotate(${rotation}deg)` }" alt="Колесо удачи">
            <button class="button" @click="spinWheel" :disabled="isSpinning">Крутить</button>
        </div>
    </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import wheelImage from '../assets/whell.png';
import arrow from '../assets/arrow.png'

const isSpinning = ref(false);
const isFirstRotation = ref(true);
const rotation = ref(0);
const shift = ref(22.5)

onMounted(() => {
    isFirstRotation.value = true;
})


const spinWheel = () => {
    if (!isSpinning.value) {
        isSpinning.value = true;
        let randomRotation = 0;
        if (isFirstRotation.value) {
            shift.value = 11.25;
            isFirstRotation.value = false;
            randomRotation = shift.value * (Math.floor(Math.random() * 8) * 2 + 1) + 1800;
        } else {
            shift.value = 22.5;
            randomRotation = shift.value * Math.floor(Math.random() * 16) + 1800;

        }


        console.log(randomRotation);

        rotation.value += randomRotation;
        setTimeout(() => {
            isSpinning.value = false;
        }, 8000);
    }
};



</script>


<style scoped>
.wheel-container {
    position: relative;
    width: 400px;
    height: 400px;
}

.wheel {
    width: 100%;
    height: 100%;
    transition: transform 8s ease-out;
    transform: rotate(5deg)
}


.button {
    background-color: #FF0000;
    color: white;
    font-family: Arial, sans-serif;
    font-size: 16px;
    margin-top: 70px;
    padding: 10px 20px;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    outline: none;
    transition: background-color 0.3s, transform 0.3s;
    box-shadow: 0 0 10px 1px white;
}

.button:hover {

    background-color: #FF3333;
    transform: scale(1.1);
}




.arrow {
    position: absolute;
    top: -120px;
    right: 160px;
    animation: arrowUpDown 2s ease-in-out infinite alternate;
}

@keyframes arrowUpDown {
    0% {
        transform: translateY(0);
    }

    100% {
        transform: translateY(20px);
    }
}
</style>