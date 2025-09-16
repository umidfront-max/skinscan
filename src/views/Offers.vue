<script setup>
import { ref } from 'vue'
import BuyerSingleCard from '@/components/BuyerSingleCard.vue'
import InputRange from '@/components/InputRange.vue'
import Containers from '@/components/Containers.vue'
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
])
</script>

<template>
  <div class="flex gap-2">
    <div class="w-[324px]">
      <BuyerSingleCard />
      <div class="flex flex-col gap-1">
        <div
          class="flex justify-between rounded-2xl transition p-4 bg-black-700 hover:bg-[#F16001]"
        >
          <p class="font-montserrat-300">Factory new</p>
          <p class="font-montserrat-300">$1,392.35</p>
        </div>
        <div
          class="flex justify-between rounded-2xl transition p-4 bg-black-700 hover:bg-[#F16001]"
        >
          <p class="font-montserrat-300">Field-tested</p>
          <p class="font-montserrat-300">$409.72</p>
        </div>
        <div
          class="flex justify-between rounded-2xl transition p-4 bg-black-700 hover:bg-[#F16001]"
        >
          <p class="font-montserrat-300">Well-worn</p>
          <p class="font-montserrat-300">$264.40</p>
        </div>
        <div
          class="flex justify-between rounded-2xl transition p-4 bg-black-700 hover:bg-[#F16001]"
        >
          <p class="font-montserrat-300">Battle-scared</p>
          <p class="font-montserrat-300">$214.42</p>
        </div>
      </div>
      <InputRange />
      <Containers />
    </div>
    <div class="bg-black grow-1 flex-1 min-h-screen text-white p-6">
      <div class="flex gap-2 mb-6">
        <p class="font-montserrat-500 !text-base italic">ACTIVE OFFERS</p>
        <img class="w-3 -mt-1" src="@/assets/img/received.svg" alt="" />
      </div>

      <!-- Offers list -->
      <div class="space-y-6 overflow-hidden">
        <div v-for="(offer, ind) in offers" :key="offer.id" :class="['relative']">
          <div class="" v-if="ind == 0">
            <svg
              viewBox="0 0 752 82"
              id="preview"
              xmlns="http://www.w3.org/2000/svg"
              class="max-h-[70vh] absolute top-0 overflow-visible"
            >
              <defs>
                <!-- Gradient chapdan o‘ngga, ranglar almashgan -->
                <linearGradient id="borderGradient" x1="0%" y1="0%" x2="100%" y2="0%">
                  <stop offset="0%" stop-color="#C10801" />
                  <stop offset="100%" stop-color="#F16001" />
                </linearGradient>

                <!-- Grid pattern -->
                <pattern id="grid" width="10" height="10" patternUnits="userSpaceOnUse">
                  <path
                    d="M 10 0 L 0 0 0 10"
                    fill="none"
                    stroke="#513d34"
                    opacity="0.2"
                    stroke-width="0.5"
                  />
                </pattern>
              </defs>

              <!-- Grid background -->
              <rect width="90000" height="90000" class="-translate-[45000px]" fill="url(#grid)" />

              <!-- Main shape -->
              <path
                d="M11,0H560A12,12 0,0,1 572,12V12A10,10 0,0,0 582,22H740A12,12 0,0,1 752,34V71A11,11 0,0,1 741,82H11A11,11 0,0,1 0,71V11A11,11 0,0,1 11,0Z"
                fill="url(#borderGradient)"
                stroke="url(#borderGradient)"
                stroke-width="0.5"
              />

              <!-- Inner path -->
              <path
                class="inner-path"
                d="M11,1H560A11,11 0,0,1 571,12V12A11,11 0,0,0 582,23H740A11,11 0,0,1 751,34V71A10,10 0,0,1 741,81H11A10,10 0,0,1 1,71V11A10,10 0,0,1 11,1Z"
                fill="black"
                stroke="url(#borderGradient)"
                stroke-width="0.5"
              />

              <!-- Optional handlers -->
              <g stroke="dodgerblue" fill="none" stroke-width=".5%" stroke-linecap="round">
                <path class="hidden" d="M1 11 A10 10 0 0 1 11 1" />
                <path class="hidden" d="M741 1 A10 10 0 0 1 751 11" />
                <path class="hidden" d="M741 81 A10 10 0 0 0 751 71" />
                <path class="hidden" d="M11 81 A10 10 0 0 1 1 71" />
              </g>

              <g class="fill-coffee stroke-gray-300 handlers" stroke-width=".3%">
                <circle data-index="0" cx="11" cy="11" />
                <circle data-index="2" cx="741" cy="71" />
                <circle data-index="3" cx="11" cy="71" />
              </g>
            </svg>

            <!-- Recommended badge -->
            <div v-if="offer.recommended" class="recommended-label">RECOMMENDED OFFER</div>
            <div class="flex relative z-1 justify-between items-end p-6 pt-5">
              <div>
                <h3 class="text-lg font-montserrat-500 flex items-center gap-2">
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
                    <i v-else class="fas fa-star text-gray-400"></i>
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
                  class="border cursor-pointer rounded-3xl flex gap-1.5 border-black-600 py-3 px-6 bg-black-800 text-xs hover:bg-black-600"
                >
                  <img v-if="!ind" src="@/assets/img/flash.svg" alt="" />
                  <img v-else src="@/assets/img/send.svg" alt="" />
                  <span>{{ offer.type }}</span>
                </button>
                <button class="px-4 cursor-pointer py-2 rounded-3xl bg-orange-500 hover:bg-orange-600 text-white">
                  Sell
                </button>
              </div>
            </div>
          </div>

          <!-- Left part -->
          <div v-else class="flex justify-between p-6 rounded-2xl bg-black-700 items-center">
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
                  <i v-else class="fas fa-star text-gray-400"></i>
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
                class="border rounded-3xl flex gap-1.5 border-black-600 py-3 px-6 bg-black-800 text-xs hover:bg-black-600"
              >
                <img v-if="!ind" src="@/assets/img/flash.svg" alt="" />
                <img v-else src="@/assets/img/send.svg" alt="" />
                <span>{{ offer.type }}</span>
              </button>
              <button class="px-4 py-2 rounded-3xl bg-orange-500 hover:bg-orange-600 text-white">
                Sell
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
@import url('https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css');

/* Box with "cut corner" */
.recommended-box {
  position: relative;
}

*::before,
*::after {
  box-sizing: border-box;
}

body {
  background: #111;
  color: #fff;
  font-family: Arial, sans-serif;
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
}

.card {
  position: relative;
  width: 400px;
  padding: 2rem;
  background: #222;
  border: 2px solid orange;
  overflow: hidden;
}

/* umumiy effekt */
[class^='invert'],
[class^='invert']::before {
  backface-visibility: hidden;
  transform: translateZ(0) translate(0, 0);
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  will-change: transform, clip-path;
}

[class^='invert'] {
  clip-path: inset(0);
  will-change: transform, clip-path;
}

/* Chap yuqori */
.invert-1::before {
  border-radius: 25px 0 0 25px;
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 50px;
  height: 50px;
  background: transparent;
  box-shadow: 0 0 0 50px #111;
  pointer-events: none;
}

/* O‘ng yuqori */
.invert-3::before {
  border-radius: 0 25px 0 0;
  content: '';
  position: absolute;
  top: 0;
  right: 0;
  width: 50px;
  height: 50px;
  background: transparent;
  box-shadow: 0 0 0 50px #111;
  pointer-events: none;
}

/* Chap pastki */
.invert-4::before {
  border-radius: 0 0 0 25px;
  content: '';
  position: absolute;
  bottom: 0;
  left: 0;
  width: 50px;
  height: 50px;
  background: transparent;
  box-shadow: 0 0 0 50px #111;
  pointer-events: none;
}

/* O‘ng pastki */
.invert-6::before {
  border-radius: 0 25px 25px 0;
  content: '';
  position: absolute;
  bottom: 0;
  right: 0;
  width: 50px;
  height: 50px;
  background: transparent;
  box-shadow: 0 0 0 50px #111;
  pointer-events: none;
}

.label {
  position: absolute;
  top: 0;
  right: 20px;
  background: #111;
  color: orange;
  font-weight: bold;
  font-size: 12px;
  padding: 4px 12px;
  font-style: italic;
}
.inverted-radius {
  --r: 20px; /* radius */
  --s: 30px; /* ichki radius */
  --x: 20px; /* gorizontal offset */
  --y: 10px; /* vertikal offset */
  --border: 3px; /* border qalinligi */
  --border-color: #f97316; /* border rangi (orange) */
  --bg: #3fb8af; /* ichki fon rangi */

  position: relative;
  width: 250px;
  aspect-ratio: 1;
}

/* Border layer */
.inverted-radius::before {
  content: '';
  position: absolute;
  inset: 0;
  background: var(--border-color);
  border-radius: var(--r);
}

/* Content layer with mask */
.inverted-radius::after {
  content: '';
  position: absolute;
  inset: var(--border);
  background: var(--bg);
  border-radius: calc(var(--r) - var(--border));

  --_m: /calc(2 * var(--r)) calc(2 * var(--r)) radial-gradient(#000 70%, #0000 72%);
  --_g: conic-gradient(at calc(100% - var(--r)) var(--r), #0000 25%, #000 0);
  --_d: (var(--s) + var(--r));
  mask:
    calc(100% - var(--_d) - var(--x)) 0 var(--_m),
    100% calc(var(--_d) + var(--y)) var(--_m),
    radial-gradient(var(--s) at 100% 0, #0000 99%, #000 calc(100% + 1px))
      calc(-1 * var(--r) - var(--x)) calc(var(--r) + var(--y)),
    var(--_g) calc(-1 * var(--_d) - var(--x)) 0,
    var(--_g) 0 calc(var(--_d) + var(--y));
  mask-repeat: no-repeat;
}

.recommended-label {
  position: absolute;
  top: -1px;
  right: 12px;
  /* background: black; */
  padding: 4px 12px;
  font-style: italic;
  font-weight: 600;
  color: white;

  border-bottom: none;
  border-radius: 8px 8px 0 0;
}

/* Optional: curved cut look */
.recommended-box::before {
  content: '';
  position: absolute;
  top: 0;
  right: 0;
  width: 90px;
  height: 32px;
  border-top: 2px solid #f97316;
  border-right: 2px solid #f97316;
  border-top-right-radius: 16px;
}
</style>
