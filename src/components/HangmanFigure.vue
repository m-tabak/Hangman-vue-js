<script setup>
import { computed, onMounted, ref } from "vue"
// SVG parts
const noosePole = '<rect fill="#000000" height="10" id="svg_11" stroke="#000000" stroke-dasharray="null" stroke-linecap="null" stroke-linejoin="null" stroke-opacity="null" stroke-width="5" width="122" x="1" y="58"/><rect fill="#000000" height="18" id="svg_14" stroke="#000000" stroke-dasharray="null" stroke-linecap="null" stroke-linejoin="null" stroke-opacity="null" stroke-width="5" transform="rotate(90, 11, 200.4)" width="262" x="-120" y="191.4"/>'
const nooseRope = '<line fill="none" fill-opacity="null" id="svg_13" stroke="#000000" stroke-dasharray="null"stroke - linecap="null" stroke - linejoin="null" stroke - opacity="null" stroke - width="2" x1 = "98" x2 = "98" y1 = "69"y2 = "121.04" />'
const head = ' <ellipse cx="99" cy="147" fill="#000000" fill-opacity="0" id="svg_1" rx="25" ry="25" stroke="#000000" stroke-width="5"/>'
const torso = '<line fill="none" fill-opacity="0" id="svg_2" stroke="#000000" stroke-dasharray="null" stroke-linecap="null" stroke-linejoin="null" stroke-opacity="null" stroke-width="5" x1="98" x2="98" y1="173" y2="258"/>'
const arm1 = ' <line fill="none" fill-opacity="0" id="svg_3" stroke="#000000" stroke-dasharray="null" stroke-linecap="null" stroke-linejoin="null" stroke-opacity="null" stroke-width="5" x1="97" x2="59" y1="195" y2="223"/>'
const arm2 = '<line fill="none" fill-opacity="0" id="svg_5" stroke="#000000" stroke-dasharray="null" stroke-linecap="null" stroke-linejoin="null" stroke-opacity="null" stroke-width="5" x1="99.2" x2="135.2" y1="195" y2="223"/>'
const leg1 = '<line fill="none" fill-opacity="0" id="svg_6" stroke="#000000" stroke-dasharray="null" stroke-linecap="null" stroke-linejoin="null" stroke-opacity="null" stroke-width="5" x1="97" x2="66" y1="258" y2="306"/>'
const leg2 = '<line fill="none" fill-opacity="0" id="svg_7" stroke="#000000" stroke-dasharray="null" stroke-linecap="null" stroke-linejoin="null" stroke-opacity="null" stroke-width="5" x1="98" x2="123" y1="258" y2="306"/>'
const deadEyes = '<line fill="none" id="svg_8" stroke="#000000" stroke-width="2" x1="112" x2="104" y1="135" y2="147"/><line fill="none" id="svg_9" stroke="#000000" stroke-width="2" x1="103.48" x2="113.11" y1="135.59" y2="146.43"/><line fill="none" id="svg_11" stroke="#000000" stroke-width="2" x1="94.8" x2="86.8" y1="135.01" y2="147.01"/><line fill="none" id="svg_10" stroke="#000000" stroke-width="2" x1="86.28" x2="95.91" y1="135.6" y2="146.45"/>'

const props = defineProps(['currentStep']) 

const currentFigure = computed(()=>{
   switch (props.currentStep) {
      case 1:
         return noosePole + head + torso + arm1
         break
      case 2:
         return noosePole + head + torso + arm1 + arm2
         break
      case 3:
         return noosePole + head + torso + arm1 + arm2 + leg1
         break
      case 4:
         return noosePole + head + torso + arm1 + arm2 + leg1 + leg2
         break
      case 5:
         return noosePole + head + torso + arm1 + arm2 + leg1 + leg2 + nooseRope +deadEyes
         break
      default:
         return noosePole + head + torso
         break
   }
})

</script>

<template>
   <svg width="200" height="400" xmlns="http://www.w3.org/2000/svg" xmlns:svg="http://www.w3.org/2000/svg">
      <g v-html="currentFigure"></g>
   </svg>
</template>

<style scoped>

</style>