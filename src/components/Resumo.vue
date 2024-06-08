<template>
  <div>
    <!-- <stepper /> -->
    <div class="flex justify-center w-full">
      <div class="flex flex-col items-center w-full md:w-9/12">
        <div class="card py-8 flex flex-col items-start px-6 w-full">
          <div class="font-bold text-left mb-8">CIA Aérea</div>
          <div class="w-full text-left">
            <div class="text-xs mb-2 font-semibold">*Nome Completo (Obrigatório)</div>
            <input
              v-model="nomeCompleto"
              class="input-base w-full"
              placeholder="Insira o seu nome"
              type="text"
            />
          </div>
          <div class="grid md:grid-cols-3 gap-6 gap-x-4 w-full mt-5">
            <div class="w-full text-left">
              <div class="text-xs mb-2 font-semibold">Fidelidade</div>
              <input
                v-model="dataNascimento"
                class="input-base w-full"
                placeholder="Insira sua data de nascimento"
                type="text"
              />
            </div>
            <div class="w-full text-left">
              <div class="text-xs mb-2 font-semibold">Senha de acesso ao site</div>
              <input
                v-model="dataNascimento"
                class="input-base w-full"
                placeholder="Insira sua data de nascimento"
                type="password"
              />
            </div>
            <div class="w-full text-left">
              <div class="text-xs mb-2 font-semibold">Qts. de CPFS</div>
              <input
                v-model="sexo"
                class="input-base w-full"
                placeholder="Insira o seu sexo"
                type="text"
              />
            </div>
            <div class="w-full text-left">
              <div class="text-xs mb-2 font-semibold">
                Melhor horário para receber o Token da Slimes
              </div>
              <input
                v-model="sexo"
                class="input-base w-full"
                placeholder="Insira o seu sexo"
                type="text"
              />
            </div>
          </div>
        </div>
        <div class="flex justify-end w-full mt-9">
          <div
            class="border-gray-700 border text-gray-700 text-center cursor-pointer w-44 mr-6 font-bold py-4 rounded-lg"
            @click="$emit('continue')"
          >
            Acessar conta
          </div>
          <div
            class="bg-primary text-center text-white cursor-pointer w-44 font-bold py-4 rounded-lg"
            @click="$emit('continue')"
          >
            Continuar
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import Stepper from './Stepper.vue'
import { ref } from 'vue'

const nomeCompleto = ref('')
const cpf = ref('')
const dataNascimento = ref('')
const sexo = ref('')
const email = ref('')
const emailConfirmacao = ref('')
const endereco = ref('')
const numero = ref('')
const complemento = ref('')
const banco = ref('')
const agencia = ref('')
const digitoAgencia = ref('')
const conta = ref('')
const digitoConta = ref('')
const contaCorrente = ref('')
const banco2 = ref('')

const emit = defineEmits(['continue'])
</script>
