<script setup>
import { onUpdated, ref } from 'vue';
const props = defineProps({
   word: String,
   missingLettersCount: Number
   })
const emit = defineEmits(['completed','gotItRight','gotItWrong'])
const formattedWord = props.word.toUpperCase()
const playingWord = ref(formattedWord)

for (let n = 0; n < props.missingLettersCount; n++) {
   playingWord.value = replaceRandomChar(playingWord.value, ' ')
}

onUpdated(()=>{
   // Give the browser time to render changes
   setTimeout(()=>{
   if(playingWord.value === formattedWord){
         emit('completed')
      }
   },100)
})

function onDrop(e, index) {
   const letter = e.dataTransfer.getData('letter')
   matchLetter(letter, index)
}

function matchLetter(letter, index){
   if(formattedWord[index]===letter){
      playingWord.value = setCharAt(playingWord.value, index, letter)
      emit('gotItRight')
   }else{
      emit('gotItWrong')
   }
}

function replaceRandomChar(str, chr){
   let index = -1
   while(index<0 || str[index]==chr){
      index = getRandomInt(str.length)
   }
   return setCharAt(str,index,chr)
}

function getRandomInt(max) {
  return Math.floor(Math.random() * max);
}

function setCharAt(str,index,chr) {
    if(index > str.length-1) return str;
    return str.substring(0,index) + chr + str.substring(index+1);
}
</script>

<template>
   <div class="word-container">
      <div 
      v-for="(letter, index) in playingWord" 
      :key="index" class="word-letter" 
      :class="{'empty-letter': letter==' '}"
      @drop="onDrop($event, index)"
      @dragover.prevent
      @dragenter.prevent>
      {{ letter }}
   </div>
   </div>
</template>

<style scoped>
   .word-container{
      display: flex;
      margin: 50px;
      padding: 0 30px;
      align-items: center;
   }
   .word-letter{
      margin: 3px;
      text-align: center;
      font-size: x-large;
      width: 30px;
      height: 30px;
   }
   .empty-letter{
      background: rgb(181, 181, 181);
   }
</style>