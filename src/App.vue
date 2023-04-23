<script setup>
import Header from "./components/Header.vue"
import Rules from "./components/Rules.vue"
import Ele from "./components/Element.vue"
</script>

<template>
  <div class="app">
    <Header />
    <Rules />
    <div class="play-area">
      <div class="interactive-area">
        <Ele class="paper" ElementImage="/images/icon-paper.svg" type="paper" />
        <Ele class="scissors" ElementImage="/images/icon-scissors.svg" type="sci" />
        <Ele class="rock" ElementImage="/images/icon-rock.svg" type="rock" />
      </div>
      <img class="triangle" src="/images/bg-triangle.svg" alt="">
    </div>
  </div>
</template>

<style scoped>
.play-area {
  margin-top: 60px;
  width: 480px;
  height: 430px;
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
}

.interactive-area {
  position: absolute;
}

.scissors {
  position: relative;
  left: 140px;
  top: -115px;
}

.paper {
  position: relative;
  left: -140px;
  top: 85px;
}

.rock {
  position: relative;
  top: -94px;
}
</style>