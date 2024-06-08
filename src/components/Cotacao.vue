<template>
  <div class="text-center">
    <div class="text-lg font-bold mb-1 text-gray-700">Venda suas milhas pelo melhor preço</div>
    <div class="text-sm">
      Selecione até 3 CIAS aéreas para fazer a cotação e escolha a forma de pagamento.
    </div>
    <div class="flex justify-center overflow-hidden">
      <div v-dragscroll class="flex gap-x-3 md:gap-x-5 overflow-x-hidden p-2 my-9 cursor-move">
        <div
          v-for="({ logo, label, classes }, i) in brands"
          :key="i"
          class="flex flex-col items-center px-1 py-3 md:p-5 min-w-24 md:min-w-52 cursor-pointer card"
        >
          <img :src="logo" :class="classes" alt="" />
          <div v-html="label" class="text-gray-700 text-xs md:text-lg leading-4 font-semibold" />
        </div>
      </div>
    </div>
    <div class="flex justify-center w-full">
      <div class="flex flex-col items-center w-11/12 md:w-8/12">
        <div class="card py-5 md:py-10 flex flex-col items-center px-8 md:px-20 w-full">
          <img src="@/assets/smiles.png" class="h-32 -mt-8 md:h-52 md:-mt-12 -mb-2" alt="" />
          <div class="w-full relative mb-16">
            <div
              @click="() => (quantity ? quantity-- : '')"
              class="text-4xl cursor-pointer font-semibold pb-4 text-primary absolute left-0"
            >
              -
            </div>
            <div
              @click="quantity++"
              class="text-4xl cursor-pointer font-semibold pb-4 text-primary absolute right-0"
            >
              +
            </div>
            <input
              type="text"
              class="focus:outline-none border-b-2 text-xl font-semibold pb-4 border-primary w-full text-center"
              v-model="quantity"
            />
          </div>
          <div
            class="card cursor-pointer items-center mb-6 px-4 py-8 w-9/12 md:w-6/12 xl:4/12 border border-primary flex justify-between"
            v-for="i in 5"
            :key="i"
            @click="checkedOption = i"
          >
            <input
              type="radio"
              :checked="checkedOption === i"
              :value="i"
              name=""
              class="radio h-5 w-5"
            />
            <div class="">
              <div class="text-lg font-bold text-primary">3 dias úteis</div>
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
          @click="emit('continue')"
        >
          Confirmar
        </div>
      </div>
    </div>
  </div>
</template>
<script setup lang="ts">
import { ref } from 'vue'
const quantity = ref(0)
const selectedBrands = ref([])
const checkedOption = ref(0)
const name = ref('')
const email = ref('')
const emit = defineEmits(['continue'])
function numberToBrl(value: number) {
  return value.toLocaleString('pt-br', { style: 'currency', currency: 'BRL' })
}
function toggleBrandSelection(params: string) {
  if (selectedBrands.value) {
  }
}
const brands = ref([
  {
    logo: '/src/assets/latam.png',
    classes: 'h-10 md:h-16 -mb-1 -mt-1',
    label: 'Latam Airlines <br/> pass'
  },
  {
    logo: '/src/assets/smiles.png',
    classes: 'h-16 -mt-4 -mb-4 md:h-24 md:-mb-6 md:-mt-5',
    label: 'Gol Linhas <br/> Aéreas'
  },
  {
    logo: '/src/assets/azul.png',
    classes: 'h-8 md:h-14 mb-1 -mt-1',
    label: 'Azul linhas <br/> Aéreas'
  },
  {
    logo: '/src/assets/miles.png',
    classes: 'h-12 -mt-2 -mb-3 md:h-28 w-10/12 md:-mt-8 md:-mb-6',
    label: 'TAP Air <br/> Portugal'
  },
  {
    logo: '/src/assets/livelo.png',
    classes: 'h-9 md:h-16 -mt-1 md:mb-1',
    label: 'BB e <br/> Bradesco'
  },
  {
    logo: '/src/assets/esfera.png',
    classes: 'md:h-7 w-8/12 mt-4 mb-3',
    label: 'Santander'
  }
])
</script>
