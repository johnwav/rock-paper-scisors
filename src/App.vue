<script setup>
import { ref, watch, computed, reactive } from 'vue'
import Header from "./components/Header.vue"
import Rules from "./components/Rules.vue"
import Control from "./components/Element.vue"
import RulesBackdrop from "./components/RulesBackdrop.vue"

const rulesOpen = ref(false)
const step = ref(1)
const UserSelect = ref('')
const CPUSelect = ref('')
const elementImage = ref('')
const elementImageCPU = ref('')
const cpuLoaded = ref(false)
const CPUtype = ref('loading')
const options = ['rock', 'paper', 'sci']


const score = ref(0)

const win = ref('')

// const selectForCPU = computed(() => {
//   return options[Math.floor(Math.random() * options.length)]
// })


const addScore = () => {
  if (UserSelect.value === CPUSelect.value) {
    win.value = "TIED"

    return score.value


  }
  if (UserSelect.value === 'paper' && CPUSelect.value === 'rock') {
    win.value = "WIN"

    return score.value++


  }

  if (UserSelect.value === 'sci' && CPUSelect.value === 'paper') {
    win.value = "WIN"

    return score.value++
  }

  if (UserSelect.value === 'rock' && CPUSelect.value === 'sci') {
    win.value = "WIN"
    cpuLoaded.value = ''
    return score.value++
  }

  else {
    win.value = "LOOSE"
  }



}

const selected = async (type) => {
  UserSelect.value = type
  cpuLoaded.value = false
  setTimeout(() => {
    CPUSelect.value = options[Math.floor(Math.random() * options.length)]
    cpuLoaded.value = true
    return CPUSelect.value
  }, 1000)
  step.value = 2
  setTimeout( async () => {
    step.value = 3
    await addScore()
    CPUSelect.value = ''
  }, 1000)
}

watch(UserSelect, () => {
  if (UserSelect.value == "paper") {
    elementImage.value = "/images/icon-paper.svg"
  }
  else if (UserSelect.value == "sci") {
    elementImage.value = "/images/icon-scissors.svg"
  }
  else if (UserSelect.value == "rock") {
    elementImage.value = "/images/icon-rock.svg"
  }
})

watch(CPUSelect, () => {
  if (CPUSelect.value == "paper") {
    elementImageCPU.value = "/images/icon-paper.svg"
    CPUtype.value = 'paper'
  }
  else if (CPUSelect.value == "sci") {
    elementImageCPU.value = "/images/icon-scissors.svg"
    CPUtype.value = 'sci'

  }
  else if (CPUSelect.value == "rock") {
    elementImageCPU.value = "/images/icon-rock.svg"
    CPUtype.value = 'rock'

  }
})


</script>
<template>
  <div class="app">
    <Header :scoredata="score" />
    <Rules @click="rulesOpen = true" />
    <div class="play-area" v-if="step === 1">
      <div class="interactive-area">
        <Control class="paper" ElementImage="/images/icon-paper.svg" type="paper" @played="selected" />
        <Control class="scissors" ElementImage="/images/icon-scissors.svg" type="sci" @played="selected" />
        <Control class="rock" ElementImage="/images/icon-rock.svg" type="rock" @played="selected" />
      </div>
      <img class="triangle" src="/images/bg-triangle.svg" alt="">
    </div>


    <div class="step2" v-if="step === 2 || step === 3">
      <div class="container">
        <div class="left">
          <h2>YOU PICKED</h2>
          <div>
            <Control size="large" :type="UserSelect" :ElementImage="elementImage" />
          </div>
        </div>
        <div class="results" v-if="step === 3">
          <h1>YOU {{ win }}</h1>
          <div @click="step = 1"> <a class="cta">PLAY AGAIN</a> </div>
        </div>
        <div class="right">
          <h2>THE HOUSE PICKED</h2>
          <Control v-if="!cpuLoaded" />
          <Control size="large" v-if="cpuLoaded" :type="CPUtype" :ElementImage="elementImageCPU" />
        </div>
      </div>
    </div>
    <RulesBackdrop v-if="rulesOpen" @rulesToggle="rulesOpen = !rulesOpen" />
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

.step2 {
  margin-top: 80px;
}

.step2 .container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 8vw;
}

.left,
.right {
  color: white;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: clamp(12vh, 80px, 40vh);
}

.results {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 20px;
}

.results h1 {
  text-align: center;
  color: white;
  font-size: 40px;
}

.results div {
  width: 218px;
  height: 42px;
  display: flex;
  align-items: center;
  justify-content: center;
  background-color: #fff;
  border-radius: 10px;
  cursor: pointer;
}

.cta {
  color: var(--DarkText);
  padding: 10px;
}

.cta :hover {
  color: red;
}
</style>