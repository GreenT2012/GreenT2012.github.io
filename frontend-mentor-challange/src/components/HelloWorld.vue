<script setup>
import { ref } from 'vue'


defineProps({
  msg: String,


})



const count = ref(0)
const previousActiveNumber =ref(0);
const state = ref(0)


function setCountAndHighlight(i) {
  this.count = i;
  this.previousActiveNumber = this.count; // Speichere die aktuelle aktive Nummer
  this.activeNumber = i;
  console.log(this.count);
}

</script>

<template>
  <div v-if="state === 0" class="original-bg container flex mx-auto p-5 bg-black sm:w-96 w-85 h-96  rounded-3xl flex-col justify-around ">
    <img class="rounded-full medium-gray w-10 p-3" src="../assets/icon-star.svg" alt="">
    <div class=" container mx-auto ">
      <h3 class="text-left text-3xl font-bold mb-3">How did we do?</h3>
      <p class="text-color font-bold text-sm text-left pl-px">Please let us know how we did with your support request.
        All feedback is appreciated to help us improve our offering!</p>
    </div>
    <div class="text-color container numbers flex flex-row justify-center  gap-6">
      <div
        v-for="i in 5"
        :key="i"
        @click="setCountAndHighlight(i);"
        :class="['circle', 'flex', 'container', 'medium-gray', 'font-bold', 'rounded-full', 'w-12', 'h-12', 'justify-center', 'items-center', (i === count ? 'active-number' : ''), ]">
      {{i}}
      </div>
    </div>
    <button @click="state=1"
            class="bg-orange-500 hover:text-orange-500 border-0 hover:bg-white rounded-full uppercase tracking-widest-xl text-sm h-12 md:h-auto font-normal ">Submit</button>
  </div>
    <div v-else class="original-bg container flex mx-auto p-5 bg-black w-96 h-96  rounded-3xl flex-col justify-around pt-8 pb-8">
    <img class="w-40 mx-auto  " src="../assets/illustration-thank-you.svg" alt="">
  <div class="banner medium-gray rounded-3xl text-orange-400 w-48  mx-auto py-2">You selected {{count}} out of 5</div>
    <h3 class="  text-3xl font-bold ">Thank You!</h3>
    <p class="px-5 text-color font-bold text-sm  pl-px">We appreciate you taking the time to give a rating. If you ever need more support,
      don’t hesitate to get in touch!</p>
  </div>


  <!-- Rating state end -->

  <!-- Thank you state start -->



  <!-- Thank you state end -->
</template>


<style scoped>
@import url(https://fonts.google.com/specimen/Overpass);
/* we will explain what these classes do next! */



.circle:hover {
  background-color:hsl(217, 12%, 63%);
  cursor:pointer;
  color:white;
}
circle{
  color:hsl(216, 12%, 54%);
}

html,body {
  font-family: 'Overpass', sans-serif!important;

}
.tracking-widest-xl{
  letter-spacing: 0.2rem;
}
.medium-gray{
background-color:hsl(213, 19%, 18%);
}
.orange{
background-color:hsl(25, 97%, 53%);
}

.active-number{
  background-color:hsl(25, 97%, 53%);
  color:white;
}
.previous-active-color{
  color:white;
  background-color:hsl(217, 12%, 63%);
}

.original-bg{
  background: radial-gradient(circle at top center, hsl(213, 19%, 18%) 5%, hsl(216, 12%, 8%)115%);
}
.text-color{
color:hsl(216, 12%, 54%)
}

</style>
