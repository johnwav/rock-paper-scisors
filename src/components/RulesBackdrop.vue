<script>



</script>

<template>
    <div class="backdrop">
    </div>
    <Transition>
        <div class="modal">
            <header>
                <h1>RULES</h1>
                <div @click="$emit('rulesToggle')" class="close"><img src="/images/icon-close.svg" /></div>
            </header>
            <div>
                <img src="/images/image-rules.svg" />
            </div>
        </div>
    </Transition>
</template>


<style scoped>
.backdrop {
    position: absolute;
    width: 100vw;
    height: 100vh;
    background-color: black;
    opacity: 0.4;
    z-index: 9;
    display: flex;
    align-items: center;
    justify-content: center;
}

.modal {
    position: absolute;
    width: 402px;
    height: 416px;
    background-color: white;
    z-index: 1000000;
    opacity: 1;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    border-radius: 12px;
}

.modal header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding-inline: 30px;
    padding-block: 36px;
}

.modal header h1 {
    color: var(--DarkText);
}

.modal header div {
    cursor: pointer;
}

.modal div {
    display: flex;
    align-items: center;
    justify-content: center;
}

</style>