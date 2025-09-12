<script setup>
import { ref } from 'vue'

const offers = ref([
  {
    id: 1,
    name: 'Skinport',
    reviews: '4.9 | 33k reviews',
    rating: 5,
    price: 573,
    bestPrice: '+22% best price',
    type: 'Instant sell',
    recommended: true,
  },
  {
    id: 2,
    name: 'Buff163',
    reviews: '2.2 | 72k reviews',
    rating: 2,
    price: 573,
    type: 'Manual sell',
    recommended: false,
  },
  {
    id: 3,
    name: 'Buff163',
    reviews: '2.2 | 72k reviews',
    rating: 2,
    price: 573,
    type: 'Manual sell',
    recommended: false,
  },
  {
    id: 4,
    name: 'Buff163',
    reviews: '2.2 | 72k reviews',
    rating: 2,
    price: 573,
    type: 'Manual sell',
    recommended: false,
  },
])
</script>

<template>
  <div class="bg-black min-h-screen text-white p-6">
    <!-- Title -->
    <h2 class="text-2xl font-bold mb-6">ACTIVE OFFERS</h2>

    <!-- Offers list -->
    <div class="space-y-6">
      <div
        v-for="(offer, ind) in offers"
        :key="offer.id"
        :class="[
          'relative flex justify-between items-center p-6 rounded-2xl border',
          offer.recommended
            ? 'border-orange-500 bg-gradient-to-r from-black to-orange-950'
            : 'border-neutral-700 bg-neutral-900',
        ]"
      >
        <!-- Recommended badge -->
        <div
          v-if="offer.recommended"
          class="absolute -top-[18px] right-6 px-4 py-1 text-xs italic font-semibold text-white
                 bg-black border border-orange-500 border-b-0 rounded-t-md"
        >
          RECOMMENDED OFFER
        </div>

        <!-- Left part -->
        <div>
          <h3 class="text-lg font-semibold flex items-center gap-2">
            <img v-if="ind == 0" src="@/assets/img/a1.svg" alt="" />
            <img v-else-if="ind == 1" src="@/assets/img/a2.svg" alt="" />
            <img v-else src="@/assets/img/a3.svg" alt="" />
            {{ offer.name }}
          </h3>
          <p class="text-xs my-1 text-gray-400">{{ offer.reviews }}</p>

          <!-- Rating stars -->
          <div class="flex gap-0.5 text-orange-400 text-xs mt-1">
            <span v-for="i in 5" :key="i">
              <i v-if="i <= offer.rating" class="fas fa-star"></i>
              <i v-else class="far fa-star text-gray-600"></i>
            </span>
          </div>
        </div>

        <!-- Middle part -->
        <div class="flex items-center gap-4">
          <p class="text-sm text-gray-300">
            <span class="text-gray-500">From - </span> ${{ offer.price }}
          </p>
          <button
            v-if="offer.bestPrice"
            class="bg-green-400 text-black px-4 py-2 rounded-2xl text-xs"
          >
            {{ offer.bestPrice }}
          </button>
          <button
            v-else
            class="bg-green-400 invisible text-black px-4 py-2 rounded-2xl text-xs"
          >
            +22% best price
          </button>
        </div>

        <!-- Buttons -->
        <div class="flex items-center gap-2">
          <button
            class="border rounded-3xl flex gap-1.5 border-gray-600 py-3 px-6 bg-neutral-800 text-xs hover:bg-neutral-700"
          >
            <img v-if="!ind" src="@/assets/img/flash.svg" alt="" />
            <img v-else src="@/assets/img/send.svg" alt="" />
            <span>{{ offer.type }}</span>
          </button>
          <button
            class="px-4 py-2 rounded-3xl bg-orange-500 hover:bg-orange-600 text-white"
          >
            Sell
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<style>
@import url('https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css');
</style>
