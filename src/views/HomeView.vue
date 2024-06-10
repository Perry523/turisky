<template>
  <div id="root" class="relative">
    <div class="bg-black h-24 w-full"></div>
    <div class="relative">
      <img src="@/assets/mile_banner.png" class="h-48 md:h-80 w-full" alt="" />
      <div class="absolute left-[10%] font-bold h-full top-0 flex flex-col justify-center">
        <div class="text-xl text-gray-600 ml-2">Compre e venda</div>
        <div class="text-5xl md:text-[170px] text-primary md:leading-[150px]">Milhas</div>
      </div>
    </div>
    <stepper v-if="step > 1" :current-step="step" style="background: #f6f2e9" class="pt-9" />

    <div class="w-full px-[5%] py-5 md:px-[9%] md:py-10" style="background: #f6f2e9">
      <cotacao v-if="step === 1" @continue="nextStep" />
      <cadastro v-else-if="step === 2" @continue="nextStep" />
      <fidelidade :selected-cias="form.selectedCias" v-else-if="step === 3" @continue="nextStep" />
      <resumo :form="form" v-else-if="step === 4" />
    </div>
  </div>
</template>
<script setup lang="ts">
import { ref } from 'vue'
import Cotacao from '@/components/Cotacao.vue'
import Fidelidade from '@/components/Fidelidade.vue'
import Cadastro from '@/components/Cadastro.vue'
import Resumo from '@/components/Resumo.vue'
import Stepper from '@/components/Stepper.vue'

const selectedObject = {}
const form = ref({})
const step = ref(1)
function nextStep(data: object) {
  step.value++
  form.value = Object.assign(form.value, data)
  // console.log('form', data)
}
</script>
<style></style>
@/components/Resmo.vue
