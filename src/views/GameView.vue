<script setup>
import { onBeforeMount, ref } from "vue";
import HangmanFigure from "../components/HangmanFigure.vue"
import DragableLetters from "@/components/DragableLetters.vue";
import WordDropLetters from "@/components/WordDropLetters.vue";
import words from '../data/words.json'

const step = ref('')
const word =ref(null)

onBeforeMount(()=>{
  reset()
})

function loseLife(){
  if(step.value <= 4){
    step.value++
  }
  if(step.value == 5){
    lose()
  }
}

function lose(){
  alert('You lost!')
  reset()
}

function win(){
  alert('You won!')
  reset()
}

function reset(){
  step.value = 0
  const index = getRandomInt(words.length)
  word.value = words[index]
}

function getRandomInt(max) {
  return Math.floor(Math.random() * max);
}
</script>

<template>
  <main>
    <div>
      <HangmanFigure :current-step="step" />
    </div>
    <div>
      <word-drop-letters  :word="word" :key="word" :missing-letters-count="3" @gotItWrong="loseLife" @completed="win"/>
      <dragable-letters />
    </div>
  </main>
</template>

<style scoped>
  main{
    display: flex;
  }
</style>
