<template>
  <div>
    <!-- <stepper /> -->
    <div class="flex justify-center w-full">
      <div class="flex flex-col items-center w-full md:w-9/12">
        <div class="card py-8 flex flex-col items-start px-6 w-full">
          {{ validate }}
          <div class="font-bold text-left mb-5">Dados do programa de fidelidade</div>
          <div class="flex flex-col divide-y divide-gray-300 gap-y-5 w-full">
            <form-fidelidade
              class="pt-3"
              v-for="(cia, i) in selectedCias"
              :key="i"
              :cia="cia"
              @save="handleSave"
              :trigger-validation="validate"
              @validated="validate = false"
            />
          </div>
        </div>
        <div class="flex justify-end w-full mt-9">
          <div
            class="border-gray-700 border text-gray-700 text-center cursor-pointer w-44 mr-6 font-bold py-4 rounded-lg"
            @click="emit('continue')"
          >
            Acessar conta
          </div>
          <div
            class="bg-primary text-center text-white cursor-pointer w-44 font-bold py-4 rounded-lg"
            @click="onSubmit"
          >
            Continuar
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { useForm } from 'vee-validate'
import { ref, computed, watch } from 'vue'
import FormFidelidade from '@/components/FormFidelidade.vue'
const props = defineProps(['selectedCias'])
const validate = ref(false)
console.log('props', props.selectedCias)

const selectedCias = ref([...props.selectedCias])
const formReady = computed(() => {
  console.log(selectedCias.value)
  return selectedCias.value.every((cia) => cia.ready)
})
const emit = defineEmits(['continue'])
function handleSave(values: Record<string, any>) {
  selectedCias.value = selectedCias.value.map((cia) => {
    if (cia.id === values.id) {
      return { ...cia, ...values }
    }
    return cia
  })
}
function onSubmit() {
  if (formReady.value) emit('continue', { selectedCias: selectedCias.value })
  else validate.value = true
}
watch(() => formReady.value, onSubmit)
</script>
