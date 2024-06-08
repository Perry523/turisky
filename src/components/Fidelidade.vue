<template>
  <div>
    <!-- <stepper /> -->
    <div class="flex justify-center w-full">
      <div class="flex flex-col items-center w-full md:w-9/12">
        <div class="card py-8 flex flex-col items-start px-6 w-full">
          <div class="font-bold text-left mb-8">Dados Pessoais</div>
          <div class="w-full text-left">
            <div class="text-xs mb-2 font-semibold">*Nome Completo (Obrigatório)</div>
            <input
              v-model="nomeCompleto"
              class="input-base w-full"
              placeholder="Insira o seu nome"
              type="text"
            />
          </div>
          <div class="grid grid-cols-1 md:grid-cols-3 gap-6 gap-x-4 gap-x-4 w-full mt-5">
            <div class="w-full text-left">
              <div class="text-xs mb-2 font-semibold">CPF</div>
              <input
                v-model="cpf"
                class="input-base w-full"
                placeholder="Insira o seu CPF"
                type="text"
              />
            </div>
            <div class="w-full text-left">
              <div class="text-xs mb-2 font-semibold">Data de nascimento</div>
              <input
                v-model="dataNascimento"
                class="input-base w-full"
                placeholder="Insira sua data de nascimento"
                type="date"
              />
            </div>
            <div class="w-full text-left">
              <div class="text-xs mb-2 font-semibold">Sexo</div>
              <input
                v-model="sexo"
                class="input-base w-full"
                placeholder="Insira o seu sexo"
                type="text"
              />
            </div>
          </div>
          <div class="grid grid-cols-2 gap-x-4 w-full mt-5">
            <div class="w-full text-left">
              <div class="text-xs mb-2 font-semibold">E-mail</div>
              <input
                v-model="email"
                class="input-base w-full"
                placeholder="Insira o seu e-mail"
                type="email"
              />
            </div>
            <div class="w-full text-left">
              <div class="text-xs mb-2 font-semibold">Confirme seu E-mail</div>
              <input
                v-model="emailConfirmacao"
                class="input-base w-full"
                placeholder="Confirme o seu e-mail"
                type="email"
              />
            </div>
          </div>
          <div class="grid grid-cols-1 md:grid-cols-3 gap-6 gap-x-4 w-full mt-5">
            <div class="w-full text-left">
              <div class="text-xs mb-2 font-semibold">Endereço</div>
              <input
                v-model="endereco"
                class="input-base w-full"
                placeholder="Insira o seu endereço"
                type="text"
              />
            </div>
            <div class="w-full text-left">
              <div class="text-xs mb-2 font-semibold">Número</div>
              <input
                v-model="numero"
                class="input-base w-full"
                placeholder="Insira o número"
                type="text"
              />
            </div>
            <div class="w-full text-left">
              <div class="text-xs mb-2 font-semibold">Complemento</div>
              <input
                v-model="complemento"
                class="input-base w-full"
                placeholder="Insira o complemento"
                type="text"
              />
            </div>
          </div>
          <div class="font-bold text-left my-8">Dados para recebimento</div>
          <div class="w-full text-left">
            <div class="text-xs mb-2 font-semibold">Banco</div>
            <input
              v-model="banco"
              class="input-base w-full"
              placeholder="Insira o banco"
              type="text"
            />
          </div>
          <div class="grid md:grid-cols-9 gap-6 gap-x-4 my-5">
            <div class="w-full text-left col-span-3">
              <div class="text-xs mb-2 font-semibold">Agencia</div>
              <input
                v-model="agencia"
                class="input-base w-full"
                placeholder="Insira a agência"
                type="text"
              />
            </div>
            <div class="w-full text-left col-span-1">
              <div class="text-xs mb-2 font-semibold">Digito</div>
              <input
                v-model="digitoAgencia"
                class="input-base w-full"
                placeholder="Insira o dígito"
                type="text"
              />
            </div>
            <div class="w-full text-left col-span-2">
              <div class="text-xs mb-2 font-semibold">Conta</div>
              <input
                v-model="conta"
                class="input-base w-full"
                placeholder="Insira a conta"
                type="text"
              />
            </div>
            <div class="w-full text-left col-span-1">
              <div class="text-xs mb-2 font-semibold">Digito</div>
              <input
                v-model="digitoConta"
                class="input-base w-full"
                placeholder="Insira o dígito"
                type="text"
              />
            </div>
            <div class="w-full text-left col-span-2">
              <div class="text-xs mb-2 font-semibold">Conta Corrente</div>
              <input
                v-model="contaCorrente"
                class="input-base w-full"
                placeholder="Insira a conta corrente"
                type="text"
              />
            </div>
          </div>
          <div class="w-full text-left pb-8">
            <div class="text-xs mb-2 font-semibold">Banco</div>
            <input
              v-model="banco2"
              class="input-base w-full"
              placeholder="Insira o banco"
              type="text"
            />
          </div>
        </div>
        <div class="flex justify-end w-full">
          <div
            class="border-gray-700 border text-gray-700 text-center cursor-pointer w-44 mr-6 font-bold py-4 rounded-lg mt-16"
            @click="$emit('continue')"
          >
            Acessar conta
          </div>
          <div
            class="bg-primary text-center text-white cursor-pointer w-44 font-bold py-4 rounded-lg mt-16"
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
