<template>
<div class="flex">
    <input type="text">
 <button class="bg-[#00FFFF] p-4 rounded-full flex items-center">
  <MagnifyingGlassIcon class="h-5 w-5 mr-2" />
  Find
</button>

</div>
<div class="flex flex-col">
    <div class="bg-[#615fff] my-2 text-center text-white">01</div>
    <div class="bg-[#615fff] my-2 text-center text-white">02</div>
    <div class="bg-[#615fff] my-2 text-center text-white">03</div>      
</div>
</template>
<script>
import { MagnifyingGlassIcon } from '@heroicons/vue/24/solid';

export default {
  components: {
    MagnifyingGlassIcon
  }
}

</script>
<style>
</style>