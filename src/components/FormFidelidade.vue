<template>
  <form @submit.prevent="submit" class="w-full">
    <div class="w-full text-left">
      <div class="text-xs mb-2 font-semibold">CIA Aérea</div>
      <input
        class="input-base w-full"
        placeholder="Insira o nome da CIA Aérea"
        disabled
        :value="cia.label"
        type="text"
      />
      <span class="text-red-500 text-xs">{{ errors.ciaAerea }}</span>
    </div>
    <div class="grid md:grid-cols-3 gap-6 gap-x-4 w-full mt-5">
      <div class="w-full text-left">
        <div class="text-xs mb-2 font-semibold">Fidelidade</div>
        <input
          v-bind="fidelidade"
          class="input-base w-full"
          placeholder="Insira o número de fidelidade"
          type="text"
        />
        <span class="text-red-500 text-xs">{{ errors.fidelidade }}</span>
      </div>
      <div class="w-full text-left">
        <div class="text-xs mb-2 font-semibold">Senha de acesso ao site</div>
        <input
          v-bind="senhaAcesso"
          class="input-base w-full"
          placeholder="Insira sua senha de acesso"
          type="password"
        />
        <span class="text-red-500 text-xs">{{ errors.senhaAcesso }}</span>
      </div>
      <div class="w-full text-left">
        <div class="text-xs mb-2 font-semibold">Qts. de CPFS</div>
        <select
          v-bind="qtdCpfs"
          class="input-base w-full"
          placeholder="Insira a quantidade de CPFS"
          type="number"
        >
          <option :value="0">0</option>
          <option :value="1">1</option>
          <option :value="2">2</option>
          <option :value="3">3</option>
          <option :value="4">4</option>
          <option :value="5">5</option>
        </select>
        <span class="text-red-500 text-xs">{{ errors.qtdCpfs }}</span>
      </div>
      <div class="w-full text-left">
        <div class="text-xs mb-2 font-semibold">Melhor horário para receber o Token da Slimes</div>
        <select
          v-bind="horarioToken"
          class="input-base w-full"
          placeholder="Insira o melhor horário"
          type="text"
        >
          <option value="manha" selected>Manhã</option>
          <option value="tarde" selected>Tarde</option>
          <option value="noite" selected>Noite</option>
        </select>
        <span class="text-red-500 text-xs">{{ errors.horarioToken }}</span>
      </div>
    </div>
  </form>
</template>
<script setup lang="ts">
import { useForm } from 'vee-validate'
import { z } from 'zod'
import { toTypedSchema } from '@vee-validate/zod'
import { watch } from 'vue'
const props = defineProps(['cia', 'triggerValidation'])
const schema = z.object({
  cia: z.string({ message: 'Campo obrigatório' }),
  fidelidade: z.string({ message: 'Campo obrigatório' }),
  senhaAcesso: z.string({ message: 'Campo obrigatório' }).min(6),
  qtdCpfs: z.number().min(1, { message: 'Mínimo 1 CPF' }),
  horarioToken: z.string({ message: 'Campo obrigatório' })
})
const { handleSubmit, errors, defineInputBinds } = useForm({
  validationSchema: toTypedSchema(schema),
  initialValues: {
    cia: props.cia.label,
    qtdCpfs: 1
  }
})

// const ciaAerea = defineInputBinds('ciaAerea')
const fidelidade = defineInputBinds('fidelidade')
const senhaAcesso = defineInputBinds('senhaAcesso')
const qtdCpfs = defineInputBinds('qtdCpfs')
const horarioToken = defineInputBinds('horarioToken')

const emit = defineEmits(['save', 'validated'])
watch(
  () => props.triggerValidation,
  (value) => {
    if (value) {
      submit()
      emit('validated')
    }
  }
)
const submit = handleSubmit((values) => {
  onSubmit(values)
})
function onSubmit(values: Record<string, any>) {
  emit('save', { ...values, ready: true, id: props.cia.id })
}
</script>
