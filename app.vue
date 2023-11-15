<template>
  <div>
    <Navbar/>
    <main>
      <div class="container mx-auto px-4 my-5">
        <div class="grid grid-cols-2 gap-2">
          <div class="grid grid-cols-4 gap-3">
            <div class="col-span-4">
              <Wysiwyg v-model="text"/>
            </div>
            <select v-model="color" class="select border border-[#D2D4D7] w-full" @change="onSelectColor">
              <option class="py-5" value="null">Select Color</option>
              <option v-for="(_color, i) in colors" :key="i" :value="_color.value">{{
                  _color.title
                }}
              </option>
            </select>
            <select v-model="pattern" class="select border border-[#D2D4D7] w-full" @change="onSelectPattern">
              <option class="py-5" value="null">Select Pattern</option>
              <option v-for="i in 10" :key="i" :value="i">{{ 'Pattern ' + i }}</option>
            </select>
            <select v-model="gradient" class="select border border-[#D2D4D7] w-full" @change="onSelectGradient">
              <option class="py-5" value="null">Select Gradient</option>
              <option v-for="i in 10" :key="i" :value="i">{{ 'Gradient ' + i }}</option>
            </select>
            <select v-model="lineHeight" class="select border border-[#D2D4D7] w-full">
              <option class="py-5" disabled>Select Line Height</option>
              <option v-for="(line, i) in lineHeights" :key="i" :value="line">{{ line }}</option>
            </select>
            <input v-model="page" class="input input-bordered w-full" placeholder="Page" type="text"/>
            <input v-model="pages" class="input input-bordered w-full" placeholder="Pages" type="text"/>
          </div>
          <div class="relative border h-[560px]">
            <div :class="[color, `pattern-${pattern}`]"
                 :style="gradient ? `background: url('/images/gradients/gradient-${gradient}.png') no-repeat center center; background-size: cover;` : ''"
                 class="h-full relative w-full z-1"></div>
            <div
                class="z-10 absolute top-0 right-0 left-0 bottom-0 my-auto mx-auto w-4/5 h-auto border border-[rgba(255,255,255,0.35)] backdrop-blur-[10px] max-h-[400px] bg-[rgba(255,255,255,0.40)] p-10 rounded-xl shadow-2xl">
              <pre :style="{lineHeight: lineHeight}" class="font-sans text-gray-800 overflow-hidden max-h-[317px]"
                   v-html="text"/>
              <div v-if="page && +page > 0 && +page <= +pages" class="absolute bottom-3 right-3 flex items-center">
                  <span class="mr-2 text-xs text-gray-500">
                    Page {{ page }}/{{ pages }}
                  </span>
                <div v-if="+page > 0 && +page < +pages" class="flex items-center">
                  <svg height="24" viewBox="0 0 24 24" width="24" xmlns="http://www.w3.org/2000/svg">
                    <g fill="none" stroke="#6b7280" stroke-width="1.5">
                      <circle cx="5" cy="12" r="2"/>
                      <circle cx="12" cy="12" opacity=".5" r="2"/>
                      <circle cx="19" cy="12" r="2"/>
                    </g>
                  </svg>
                  <span class="ml-2">
                    <svg height="24" viewBox="0 0 24 24" width="24" xmlns="http://www.w3.org/2000/svg">
                    <path d="M4 12h2.5M20 12l-6-6m6 6l-6 6m6-6H9.5" fill="none" stroke="#6b7280" stroke-linecap="round"
                          stroke-linejoin="round"
                          stroke-width="1.5"/>
                    </svg>
                  </span>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </main>
  </div>
</template>
<script lang="ts" setup>
import {ref} from "vue";

const text = ref("")
const pattern = ref<string | null>(null)
const gradient = ref<string | null>(null)
const page = ref("")
const pages = ref("")
const lineHeight = ref(1.5)
const lineHeights = [1, 1.5, 2, 2.5, 3, 3.5, 4, 4.5, 5, 5.5, 6, 6.5]
const color = ref<string | null>("bg-yellow-400")
const colors = [
  {
    title: 'Yellow',
    value: 'bg-yellow-400'
  },
  {
    title: 'Green',
    value: 'bg-green-400'
  },
  {
    title: 'Blue',
    value: 'bg-blue-400'
  }, {
    title: 'Orange',
    value: 'bg-orange-400'
  }, {
    title: 'Red',
    value: 'bg-red-400'
  }, {
    title: 'Pink',
    value: 'bg-pink-400'
  }, {
    title: 'Purple',
    value: 'bg-purple-400'
  },
];

const onSelectColor = () => {
  if (color.value) {
    // pattern.value = null
    gradient.value = null;
  } else {
    gradient.value = "1"
  }
}
const onSelectPattern = () => {
  if (pattern.value != null) {
    // color.value = null
    gradient.value = null;

    return;
  }

  color.value = "bg-yellow-400"
}
const onSelectGradient = () => {
  if (gradient.value) {
    color.value = null
    pattern.value = null;
  } else {
    color.value = "bg-yellow-400"
  }
}
</script>

<style lang="scss">
@import "assets/style.scss";
</style>