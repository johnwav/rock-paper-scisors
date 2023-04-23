<script setup>
import { reactive, ref, watch } from "vue"
const { ElementImage, type, size } = defineProps(['ElementImage', 'type', 'size'])

const styleObject = reactive({})



if (size === 'large') {
    styleObject.scale = 1.3
}

if (type === 'paper') {
    styleObject.backgroundColor = 'blue'
    styleObject.boxShadow = '0px 10px rgb(59, 17, 17)'

}

if (type === 'rock') {
    styleObject.backgroundColor = 'red'
    styleObject.boxShadow = '0px 10px rgb(59, 17, 17)'

}

if (type === 'sci') {
    styleObject.backgroundColor = 'yellow'
    styleObject.boxShadow = '0px 10px rgb(59, 17, 17)'
}

watch(type, (newValue) => {
    type.value = newValue.value
})


</script>

<template>
    <div class="element" :style="styleObject" @click="$emit('played', type)">
        <div class="wrapper">
            <img :src="ElementImage" alt="">
        </div>
    </div>
</template>

<style scoped>
.element {
    width: 200px;
    height: 200px;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    cursor: pointer;
}

.wrapper {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 152px;
    height: 152px;
    border-radius: 50%;
    background-color: white;

}

.element img {
    object-fit: contain;
    width: 60px;
}
</style>