<template>
  <div class="text-center">
    <div class="text-lg font-bold mb-1 text-gray-700">Venda suas milhas pelo melhor preço</div>
    <div class="text-sm">
      Selecione até 3 CIAS aéreas para fazer a cotação e escolha a forma de pagamento.
    </div>
    <div class="flex justify-center overflow-hidden">
      <div v-dragscroll class="flex gap-x-3 md:gap-x-5 overflow-x-hidden p-2 my-9 cursor-move">
        <div
          v-for="(brand, i) in brands"
          :key="i"
          class="flex flex-col items-center px-1 py-3 md:p-5 min-w-24 md:min-w-52 cursor-pointer card"
          @click="toggleBrandSelection(brand)"
          :class="isBrandIncluded(brand) ? 'border border-primary' : ''"
        >
          <img :src="brand.logo" :class="brand.classes" alt="" />
          <div
            v-html="brand.html"
            class="text-gray-700 text-xs md:text-lg leading-4 font-semibold"
          />
        </div>
      </div>
    </div>
    <div class="flex justify-center w-full">
      <div class="flex flex-col items-center w-11/12 md:w-8/12 gap-4">
        <div
          class="card py-5 md:py-10 flex flex-col items-center px-8 md:px-20 w-full"
          v-for="(selectedBrand, i) in selectedCias"
          :key="i"
        >
          <div
            :style="{ 'background-image': 'url(' + selectedBrand.logo + ')' }"
            class="h-32 -mt-4 md:h-52 md:-mt-9 w-full bg-no-repeat bg-contain bg-center"
            alt=""
          />
          <div class="w-full relative mb-16">
            <div
              @click="() => (selectedBrand.quantity > 50000 ? selectedBrand.quantity-- : '')"
              class="text-4xl cursor-pointer font-semibold pb-4 text-primary absolute left-0"
            >
              -
            </div>
            <div
              @click="selectedBrand.quantity++"
              class="text-4xl cursor-pointer font-semibold pb-4 text-primary absolute right-0"
            >
              +
            </div>
            <input
              type="text"
              class="focus:outline-none border-b-2 text-xl font-semibold pb-4 border-primary w-full text-center"
              v-model="selectedBrand.quantity"
              :min="50000"
            />
          </div>
          <div
            class="card cursor-pointer items-center mb-6 px-4 py-8 w-9/12 md:w-6/12 xl:4/12 border border-primary flex justify-between"
            v-for="i in [3, 7, 15, 30, 45, 60]"
            :key="i"
            @click="selectedBrand.days = i"
          >
            <input
              type="radio"
              :checked="selectedBrand.days === i"
              :value="i"
              name=""
              class="radio h-5 w-5"
            />
            <div class="">
              <div class="text-lg font-bold text-primary">{{ i }} dias úteis</div>
              <div class="font-semibold text-lg leading-4">{{ numberToBrl(0) }}</div>
            </div>
          </div>
        </div>
        <div class="my-14 md:my-28 w-full flex flex-col">
          <input
            type="text"
            class="focus:outline-none text-sm placeholder:text-gray-500 placeholder:text-sm text-gray-500 bg-transparent border-b pb-2 border-primary pl-4"
            v-model="name"
            placeholder="Nome Completo"
          />
          <input
            type="text"
            class="focus:outline-none text-sm mt-12 placeholder:text-gray-500 placeholder:text-sm text-gray-500 bg-transparent border-b pb-2 border-primary pl-4"
            v-model="email"
            placeholder="E-mail"
          />
        </div>
        <div
          class="bg-primary text-center text-white cursor-pointer w-full font-bold py-5 rounded-lg"
          @click="showContinueModal = true"
        >
          Confirmar
        </div>
      </div>
    </div>
  </div>
  <continue-modal v-if="showContinueModal" @continue="next" />
</template>
<script setup lang="ts">
import { ref } from 'vue'
import ContinueModal from '@/components/ContinueModal.vue'
const selectedCias = ref<selectedBrand[]>([])
const showContinueModal = ref(false)
const name = ref('')
const email = ref('')
const emit = defineEmits(['continue'])
type brand = {
  logo: string
  classes: string
  label: string
  html: string
  id: number
}
type selectedBrand = {
  logo: string
  classes: string
  label: string
  html: string
  id: number
  quantity: number
  days: number
}
function numberToBrl(value: number) {
  return value.toLocaleString('pt-br', { style: 'currency', currency: 'BRL' })
}
function getImage(path) {
  return new URL(path, import.meta.url).href
}
function isBrandIncluded(brand: brand) {
  return selectedCias.value.some((selectedBrand) => selectedBrand.id === brand.id)
}
function toggleBrandSelection(brand: brand) {
  if (isBrandIncluded(brand)) {
    selectedCias.value = selectedCias.value.filter((selectedBrand) => selectedBrand.id !== brand.id)
  } else {
    if (selectedCias.value.length < 3)
      selectedCias.value.push(Object.assign(brand, { quantity: 50000, days: 3 }))
  }
}
const brands = ref<brand[]>([
  {
    logo: '/src/assets/latam.png',
    classes: 'h-10 md:h-16 -mb-1 -mt-1',
    html: 'Latam Airlines <br/> pass',
    label: 'Latam Airlines pass',
    id: 1
  },
  {
    logo: '/src/assets/smiles.png',
    classes: 'h-16 -mt-4 -mb-4 md:h-24 md:-mb-6 md:-mt-5',
    html: 'Gol Linhas <br/> Aéreas',
    label: 'Gol Linhas Aéreas',
    id: 2
  },
  {
    logo: '/src/assets/azul.png',
    classes: 'h-8 md:h-14 mb-1 -mt-1',
    html: 'Azul linhas <br/> Aéreas',
    label: 'Azul linhas Aéreas',
    id: 3
  },
  {
    logo: '/src/assets/miles.png',
    classes: 'h-12 -mt-2 -mb-3 md:h-28 w-10/12 md:-mt-8 md:-mb-6',
    label: 'TAP Air Portugal',
    html: 'TAP Air  <br/>  Portugal',
    id: 4
  },
  {
    logo: '/src/assets/livelo.png',
    classes: 'h-9 md:h-16 -mt-1 md:mb-1',
    html: 'BB e <br/> Bradesco',
    label: 'BB e Bradesco',
    id: 5
  },
  {
    logo: '/src/assets/esfera.png',
    classes: 'md:h-7 w-8/12 mt-4 mb-3',
    html: 'Santander',
    label: 'Santander',
    id: 6
  }
])
function next() {
  showContinueModal.value = false
  emit('continue', { name: name.value, email: email.value, selectedCias: selectedCias.value })
}
</script>
