<script setup>
import { reactive , ref} from "vue"
const {ElementImage, type} = defineProps(['ElementImage', 'type'])

const styleObject = reactive({})


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




</script>

<template>
    <div class="element" :style="styleObject">
        <div class="wrapper" >
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