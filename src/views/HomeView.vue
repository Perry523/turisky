<template>
  <div class="relative">
    <div class="bg-black h-24 w-full"></div>
    <div class="relative">
      <img src="@/assets/mile_banner.png" class="h-48 md:h-80 w-full" alt="" />
      <div class="absolute left-[10%] font-bold h-full top-0 flex flex-col justify-center">
        <div class="text-xl text-gray-600 ml-2">Compre e venda</div>
        <div class="text-5xl md:text-[170px] text-primary md:leading-[150px]">Milhas</div>
      </div>
    </div>
    <div class="w-full px-[5%] py-5 md:px-[9%] md:py-10" style="background: #f6f2e9">
      <cotacao v-if="step === 1" @continue="showContinueModal = true" />
      <fidelidade v-else-if="step === 3" @continue="nextStep" />
      <resumo v-else-if="step === 4" @continue="nextStep" />
      <venda-realizada v-else-if="step === 5" />
    </div>
    <continue-modal v-if="showContinueModal" @continue="nextStep" />
  </div>
</template>
<script setup lang="ts">
import { ref } from 'vue'
import Cotacao from '@/components/Cotacao.vue'
import ContinueModal from '@/components/ContinueModal.vue'
import Fidelidade from '@/components/Fidelidade.vue'
import Resumo from '@/components/Resumo.vue'
import VendaRealizada from '@/components/VendaRealizada.vue'

const step = ref(1)
const showContinueModal = ref(false)
function nextStep() {
  if (step.value === 1) step.value = 3
  else step.value++
  showContinueModal.value = false
}
</script>
<style></style>
