<script setup>
const alphabet=[]
for (let i = 65; i <= 90; i++) {
   alphabet.push(String.fromCharCode(i))
}

function dragStartHandler(e, letter){ 
   e.dataTransfer.setData("letter", letter)
}


</script>

<template>
   <ul class="letters-container unselectable">
      <li class="letter-box" draggable="true" v-for="letter in alphabet" :key="letter" @dragstart="dragStartHandler($event, letter)">
         {{ letter }}
      </li>
   </ul>
</template>

<style scoped>
   .letters-container{
      margin: 50px;
   }


   .letter-box{
      cursor: grab;
      display: inline-block;
      list-style: none;
      text-align: center;
      margin: 5px;
      padding: 5px 0;
      width: 1.6rem;
      height: 1.2rem;
      border: 1px solid black;
      border-radius: 3px;
   }
</style>