<script setup>
     import { computed } from '@vue/reactivity';
     import { ref, onMounted  } from 'vue';
     
     
     let id = 0
     let squareAreaInfo;
     const squaresLength = computed(() => squares.value.length)
     
     const squares = ref([
          { id: id++, size: 10 +  "px", posX: 5 +  "px", posY: 15 +  "px", color: "#" +Math.floor(Math.random()*16777215).toString(16)},
          { id: id++, size: 20 +  "px", posX: 50 +  "px", posY: 15 +  "px", color: "#" +Math.floor(Math.random()*16777215).toString(16)}
     ])
     

     const emit = defineEmits(['isFinished'])

     






     function increment(){
          squares.value.push({
               id: id++, 
               size: Math.random() * 50 + "px", 
               posX: Math.random() * squareAreaInfo.width + "px", 
               posY: Math.random() * squareAreaInfo.height + "px",
               color: "#" + Math.floor(Math.random()*16777215).toString(16)
          })
          if(squaresLength.value >= 10) {
               emit('isFinished', true, "bob", 1+1)
          }
     }

     function removeSquare(square){
          squares.value = squares.value.filter((s) => s !== square)
     }

     
     onMounted(() => {
          squareAreaInfo = document.querySelector('.squareArea').getBoundingClientRect();

     })
</script>


<template>
     <h2 @click="increment">Add square</h2>
     <div class="squareArea">
          <div v-for="square in squares" :key="square.id" 
               :style="{
                    width: square.size, 
                    height: square.size,
                    top: square.posY,
                    left: square.posX,
                    backgroundColor: square.color
               }"
               @click="removeSquare(square)">
          </div>
     </div>
</template>


<style scoped>
     h2{
          color: red;
          cursor: pointer;
     }
     a:hover{
          cursor: pointer;
          color: green;
     }
     .squareArea{
          position: relative;
          width: 60vw;
          height: 60vh;
     }
     .squareArea>div{
          position: absolute;
          cursor:pointer;
     }

</style>