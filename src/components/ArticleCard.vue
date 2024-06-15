<template>
  <div class="relative rounded-lg">
    <div
      class="rounded-lg bg-cover bg-center bg-no-repeat"
      :class="classes"
      :style="{ 'background-image': 'url(' + bgImage + ')' }"
    >
      <div class="w-full h-full bg-[#183B56] opacity-40 rounded-lg"></div>
    </div>
    <div class="absolute w-full h-full p-4 top-0 flex flex-col">
      <div>
        <span
          v-if="badge"
          class="bg-white rounded-full px-5 text-primary uppercase text-xs font-bold py-1 grow-0"
        >
          {{ badge }}
        </span>
      </div>
      <div class="mt-auto w-full px-4">
        <div class="font-bold text-white" :class="description ? 'text-xl' : 'text-2xl mb-6'">
          {{ title }}
        </div>
        <div class="text-white text-sm py-2" v-if="description">
          {{ description }}
        </div>
        <div class="flex justify-between text-white mb-4 mt-2 text-xs items-center">
          <div class="flex items-center gap-x-2">
            <img class="w-7 rounded-full" :src="authorImage" alt="" />
            <div>{{ authorName }}</div>
          </div>
          <div>
            {{ formatDate(date) }}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script setup lang="ts">
defineProps([
  'authorName',
  'authorImage',
  'bgImage',
  'title',
  'date',
  'badge',
  'description',
  'classes'
])
function formatDate(dateString: string) {
  // Separar o dia, mês e ano da string
  const [day, month] = dateString.split('/')

  // Array com os nomes dos meses
  const monthNames = [
    'Janeiro',
    'Fevereiro',
    'Março',
    'Abril',
    'Maio',
    'Junho',
    'Julho',
    'Agosto',
    'Setembro',
    'Outubro',
    'Novembro',
    'Dezembro'
  ]
  const monthName = monthNames[parseInt(month, 10) - 1]
  return `${day} ${monthName}`
}
</script>
