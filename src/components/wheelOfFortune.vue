<template>
    <div class="wheel-container">
        <img class='arrow' :src="arrow" alt="Стрелочка">
        <img class="wheel" :src="wheelImage" :style="{ transform: `rotate(${rotation}deg)` }" alt="Колесо удачи">
        <button class="button" @click="spinWheel" :disabled="isSpinning">Крутить</button>
    </div>
</template>

<script setup>
import { ref } from 'vue';
import wheelImage from '../assets/whell.png';
import arrow from '../assets/arrow.png'

const isSpinning = ref(false);
const rotation = ref(0);

const spinWheel = () => {
    if (!isSpinning.value) {
        isSpinning.value = true;
        const randomRotation = Math.floor(Math.random() * 360) + 760;
        rotation.value += randomRotation;
        setTimeout(() => {
            isSpinning.value = false;
        }, 3000);
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
    transition: transform 3s ease-out
}


.button {
    position: absolute;
    top: 50%;
    right: -200px;
    padding: 10px 30px;
    margin-top: 15px;
    font-size: 16px;
    background-color: #ff0000dd;
    color: #ffffff;
    border: none;
    border-radius: 10px;
    cursor: pointer;
    box-shadow: 0 0 25px 5px  rgba(255, 255, 255, 0.433);
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