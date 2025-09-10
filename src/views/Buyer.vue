<script setup>
import BuyerCard from '@/components/BuyerCard.vue'


</script>

<template>
  <div class="">
    <div class="flex justify-between items-center max-md:flex-col max-md:items-start max-md:gap-2">
      <h1
        class="text-white tracking-normal text-5xl max-[1350px]:text-4xl max-lg:text-2xl italic font-montserrat-500 uppercase proportional-nums"
      >
        Browse and Sell all CS2 & CS:GO skins
      </h1>
      <button class="btn-secondary">Advanced search</button>
    </div>
    <div
      class="grid grid-cols-4 gap-3 mt-9 max-lg:gap-2 max-md:grid-cols-3 max-sm:grid-cols-2 max-xs:grid-cols-1"
    >
      <BuyerCard />
      <BuyerCard />
      <BuyerCard />
      <BuyerCard />
      <BuyerCard />
      <BuyerCard />
      <BuyerCard />
      <BuyerCard />
    </div>
  </div>
</template>
