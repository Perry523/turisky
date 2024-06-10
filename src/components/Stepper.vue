<template>
  <div class="flex justify-center relative w-full">
    <div class="flex items-start w-11/12">
      <div
        v-for="(step, i) in [
          'Cotação',
          'Cadastro',
          'Fidelidade',
          'Resumo',
          'Venda <br /> Realizada'
        ]"
        :key="i"
        class="relative z-20 col mx-auto flex flex-col items-center"
      >
        <div
          :class="currentStep >= i + 1 ? 'bg-primary ' : 'bg-gray-400'"
          class="md:text-2xl border-4 md:border-[6px] border-gray-300 rounded-full text-center w-8 md:w-12 h-8 md:h-12 text-white"
        >
          {{ i + 1 }}
        </div>
        <div
          v-html="step"
          class="md:text-sm text-center mt-2 text-xs"
          :class="currentStep >= i + 1 ? 'text-primary ' : 'text-gray-400'"
        />
      </div>
    </div>
    <div class="absolute w-full flex top-12 md:top-14 h-1 md:h-2 px-2 md:px-10">
      <div class="bg-primary rounded-lg z-10" :style="{ width: currentStep * 20 + '%' }"></div>

      <div
        class="bg-slate-300 rounded-r-lg -ml-1"
        :style="{ width: 100 - currentStep * 20 + '%' }"
      ></div>
    </div>
  </div>
</template>
<script setup lang="ts">
import { computed } from 'vue'

const props = defineProps(['currentStep'])
</script>
