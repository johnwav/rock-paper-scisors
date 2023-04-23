<script setup></script>

<template>
    <div class="title-box">
        <h1>
            ROCK <br>
            PAPER <br>
            SCISSORS
        </h1>
        <div class="score-board">
            <span>SCORE</span>
            <h2>12</h2>
        </div>
    </div>
</template>

<style scoped>
.title-box {
    margin-top: 36px;
    width: 702px;
    height: 148px;
    border: 2.5px solid var(--HeaderOutline);
    border-radius: 20px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding-inline: 32px;
}

.title-box h1 {
    color: white;
    font-size: 38px;
    font-weight: 700;
    line-height: 30px;
}

.score-board {
    width: 152px;
    height: 116px;
    background-color: white;
    border-radius: 10px;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
}

.score-board h2 {
    font-size: 66px;
    color: var(--DarkText);
    margin-top: -10px;
}

.score-board span {
    color: var(--ScoreText);
    letter-spacing: 2px;

}
</style>