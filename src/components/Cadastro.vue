<template>
  <div>
    <div class="flex justify-center w-full">
      <div class="flex flex-col items-center w-full md:w-9/12">
        <div class="card py-8 flex flex-col items-start px-6 w-full">
          <div class="font-bold text-left mb-8">Dados Pessoais</div>
          <form @submit.prevent="submit" class="w-full">
            <div class="w-full text-left">
              <div class="text-xs mb-2 font-semibold">Nome Completo</div>
              <input
                v-bind="nomeCompleto"
                class="input-base w-full"
                placeholder="Insira o seu nome"
                type="text"
              />
              <span class="text-red-500 text-xs">{{ errors.nomeCompleto }}</span>
            </div>
            <div class="grid grid-cols-1 md:grid-cols-3 gap-6 gap-x-4 w-full mt-5">
              <div class="w-full text-left">
                <div class="text-xs mb-2 font-semibold">CPF</div>
                <input
                  v-bind="cpf"
                  data-maska="#-#"
                  class="input-base w-full"
                  placeholder="Insira o seu CPF"
                  type="text"
                />
                <span class="text-red-500 text-xs">{{ errors.cpf }}</span>
              </div>
              <div class="w-full text-left">
                <div class="text-xs mb-2 font-semibold">Data de nascimento</div>
                <input
                  v-bind="dataNascimento"
                  class="input-base w-full"
                  placeholder="Insira sua data de nascimento"
                  type="date"
                />
                <span class="text-red-500 text-xs">{{ errors.dataNascimento }}</span>
              </div>
              <div class="w-full text-left">
                <div class="text-xs mb-2 font-semibold">Sexo</div>
                <select
                  v-bind="sexo"
                  class="input-base w-full fill-orange-500"
                  placeholder="Insira o seu sexo"
                  type="text"
                >
                  <option value="" selected>Selecione</option>
                  <option value="masculino">Masculino</option>
                  <option value="feminino">Feminino</option>
                  <option value="outro">Outro</option>
                </select>
                <span class="text-red-500 text-xs">{{ errors.sexo }}</span>
              </div>
            </div>
            <div class="grid grid-cols-2 gap-x-4 w-full mt-5">
              <div class="w-full text-left">
                <div class="text-xs mb-2 font-semibold">E-mail</div>
                <input
                  v-bind="email"
                  class="input-base w-full"
                  placeholder="Insira o seu e-mail"
                  type="email"
                />
                <span class="text-red-500 text-xs">{{ errors.email }}</span>
              </div>
              <div class="w-full text-left">
                <div class="text-xs mb-2 font-semibold">Confirme seu E-mail</div>
                <input
                  v-bind="emailConfirmacao"
                  class="input-base w-full"
                  placeholder="Confirme o seu e-mail"
                  type="email"
                />
                <span class="text-red-500 text-xs">{{ errors.emailConfirmacao }}</span>
              </div>
            </div>
            <div class="grid grid-cols-1 md:grid-cols-3 gap-6 gap-x-4 w-full mt-5">
              <div class="w-full text-left">
                <div class="text-xs mb-2 font-semibold">Endereço</div>
                <input
                  v-bind="endereco"
                  class="input-base w-full"
                  placeholder="Insira o seu endereço"
                  type="text"
                />
                <span class="text-red-500 text-xs">{{ errors.endereco }}</span>
              </div>
              <div class="w-full text-left">
                <div class="text-xs mb-2 font-semibold">Número</div>
                <input
                  v-bind="numero"
                  class="input-base w-full"
                  placeholder="Insira o número"
                  type="text"
                />
                <span class="text-red-500 text-xs">{{ errors.numero }}</span>
              </div>
              <div class="w-full text-left">
                <div class="text-xs mb-2 font-semibold">Complemento</div>
                <input
                  v-bind="complemento"
                  class="input-base w-full"
                  placeholder="Insira o complemento"
                  type="text"
                />
                <span class="text-red-500 text-xs">{{ errors.complemento }}</span>
              </div>
            </div>
            <div class="font-bold text-left my-8">Dados para recebimento</div>
            <div class="w-full text-left">
              <div class="text-xs mb-2 font-semibold">Banco</div>
              <input
                v-bind="banco"
                class="input-base w-full"
                placeholder="Insira o banco"
                type="text"
              />
              <span class="text-red-500 text-xs">{{ errors.banco }}</span>
            </div>
            <div class="grid md:grid-cols-9 gap-6 gap-x-4 my-5">
              <div class="w-full text-left col-span-3">
                <div class="text-xs mb-2 font-semibold">Agencia</div>
                <input
                  v-bind="agencia"
                  class="input-base w-full"
                  placeholder="Insira a agência"
                  type="text"
                />
                <span class="text-red-500 text-xs">{{ errors.agencia }}</span>
              </div>
              <div class="w-full text-left col-span-1">
                <div class="text-xs mb-2 font-semibold">Digito</div>
                <input
                  v-bind="digitoAgencia"
                  class="input-base w-full"
                  placeholder="Insira o dígito"
                  type="text"
                />
                <span class="text-red-500 text-xs">{{ errors.digitoAgencia }}</span>
              </div>
              <div class="w-full text-left col-span-2">
                <div class="text-xs mb-2 font-semibold">Conta</div>
                <input
                  v-bind="conta"
                  class="input-base w-full"
                  placeholder="Insira a conta"
                  type="text"
                />
                <span class="text-red-500 text-xs">{{ errors.conta }}</span>
              </div>
              <div class="w-full text-left col-span-1">
                <div class="text-xs mb-2 font-semibold">Digito</div>
                <input
                  v-bind="digitoConta"
                  class="input-base w-full"
                  placeholder="Insira o dígito"
                  type="text"
                />
                <span class="text-red-500 text-xs">{{ errors.digitoConta }}</span>
              </div>
              <div class="w-full text-left col-span-2">
                <div class="text-xs mb-2 font-semibold">Conta Corrente</div>
                <input
                  v-bind="contaCorrente"
                  class="input-base w-full"
                  placeholder="Insira a conta corrente"
                  type="text"
                />
                <span class="text-red-500 text-xs">{{ errors.contaCorrente }}</span>
              </div>
            </div>
            <div class="w-full text-left pb-8">
              <div class="text-xs mb-2 font-semibold">Chave PIX</div>
              <input
                v-bind="pix"
                class="input-base w-full"
                placeholder="Insira o banco"
                type="text"
              />
              <span class="text-red-500 text-xs">{{ errors.pix }}</span>
            </div>
            <div class="flex justify-end w-full">
              <div
                class="border-gray-700 border text-gray-700 text-center cursor-pointer w-44 mr-6 font-bold py-4 rounded-lg mt-16"
                @click="submit"
              >
                Acessar conta
              </div>
              <div
                class="bg-primary text-center text-white cursor-pointer w-44 font-bold py-4 rounded-lg mt-16"
                @click="submit"
              >
                Continuar
              </div>
            </div>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { useForm } from 'vee-validate'
import { z } from 'zod'
import { toTypedSchema } from '@vee-validate/zod'
import { watch } from 'vue'
import { vMaska } from 'maska'

// Função de validação de CPF
function isValidCPF(cpf: string): boolean {
  cpf = cpf.replace(/[^\d]/g, '') // Remove caracteres não numéricos

  if (cpf.length !== 11 || cpf.match(/(\d)\1{10}/)) return false // Verifica se o CPF tem 11 dígitos e se todos os dígitos são iguais

  let soma: number = 0
  for (let i = 0; i < 9; i++) {
    soma += parseInt(cpf.charAt(i)) * (10 - i)
  }

  let resto: number = 11 - (soma % 11)
  if (resto === 10 || resto === 11) resto = 0

  if (resto !== parseInt(cpf.charAt(9))) return false

  soma = 0
  for (let i = 0; i < 10; i++) {
    soma += parseInt(cpf.charAt(i)) * (11 - i)
  }

  resto = 11 - (soma % 11)
  if (resto === 10 || resto === 11) resto = 0

  if (resto !== parseInt(cpf.charAt(10))) return false

  return true
}

const schema = z.object({
  nomeCompleto: z.string({ message: 'Campo obrigatório' }),
  cpf: z.string({ message: 'Campo obrigatório' }).refine(isValidCPF, { message: 'CPF inválido' }),
  dataNascimento: z.string({ message: 'Campo obrigatório' }),
  sexo: z.string({ message: 'Campo obrigatório' }),
  email: z.string({ message: 'Campo obrigatório' }).email({ message: 'E-mail inválido' }),
  emailConfirmacao: z
    .string({ message: 'Campo obrigatório' })
    .email({ message: 'E-mail inválido' }),
  endereco: z.string({ message: 'Campo obrigatório' }),
  numero: z.string({ message: 'Campo obrigatório' }),
  complemento: z.string({ message: 'Campo obrigatório' }),
  banco: z.string({ message: 'Campo obrigatório' }),
  agencia: z.string({ message: 'Campo obrigatório' }),
  digitoAgencia: z.string({ message: 'Campo obrigatório' }),
  conta: z.string({ message: 'Campo obrigatório' }),
  digitoConta: z.string({ message: 'Campo obrigatório' }),
  contaCorrente: z.string({ message: 'Campo obrigatório' }),
  pix: z.string({ message: 'Campo obrigatório' })
})

const { handleSubmit, errors, defineInputBinds, setErrors } = useForm({
  validationSchema: toTypedSchema(schema)
})
const nomeCompleto = defineInputBinds('nomeCompleto')
const cpf = defineInputBinds('cpf')
const dataNascimento = defineInputBinds('dataNascimento')
const sexo = defineInputBinds('sexo')
const email = defineInputBinds('email')
const emailConfirmacao = defineInputBinds('emailConfirmacao')
const endereco = defineInputBinds('endereco')
const numero = defineInputBinds('numero')
const complemento = defineInputBinds('complemento')
const banco = defineInputBinds('banco')
const agencia = defineInputBinds('agencia')
const digitoAgencia = defineInputBinds('digitoAgencia')
const conta = defineInputBinds('conta')
const digitoConta = defineInputBinds('digitoConta')
const contaCorrente = defineInputBinds('contaCorrente')
const pix = defineInputBinds('pix')

const emit = defineEmits(['continue'])
const submit = handleSubmit((values) => {
  onSubmit(values)
})
function onSubmit(values: Record<string, any>) {
  emit('continue', values)
}

watch(emailConfirmacao, () => {
  if (emailConfirmacao.value.value !== email.value.value)
    setErrors({
      emailConfirmacao: 'Email não confere' // auto-complete for `email` and `password`
    })
})
</script>

<style scoped>
/* Seus estilos aqui */
</style>
