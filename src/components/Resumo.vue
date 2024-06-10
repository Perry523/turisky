<template>
  <div>
    <!-- <stepper /> -->
    <div class="flex justify-center w-full">
      <div class="flex flex-col items-center w-full md:w-9/12">
        <div class="card py-10 flex flex-col items-start px-6 w-full">
          <div class="font-bold text-left mb-8">Resumo da venda</div>
          <div class="text-xs mb-2">Negociações</div>
          <div
            class="py-6 w-full border border-primary grid grid-cols-2 md:flex flex-wrap gap-4 px-3 md:px-10 justify-between mb-3"
            v-for="(selectedCia, i) in form.selectedCias"
            :key="i"
          >
            <div class="text-xs md:text-sm">
              <div class="font-semibold mb-5">Cia Aérea</div>
              <div class="text-xs">
                {{ selectedCia.label }}
              </div>
            </div>
            <div class="text-xs md:text-sm">
              <div class="font-semibold mb-5">Qtda Milhas</div>
              <div class="text-xs">
                {{ selectedCia.quantity }}
              </div>
            </div>
            <div class="text-xs md:text-sm">
              <div class="font-semibold mb-5">Modo Pgto</div>
              <div class="text-xs">
                {{ `Após ${selectedCia.days} DIAS` }}
              </div>
            </div>
            <div class="text-xs md:text-sm">
              <div class="font-semibold mb-5">Total</div>
              <div class="text-xs">
                {{ numberToBrl(237) }}
              </div>
            </div>
          </div>
          <div class="text-xs mb-2 mt-3">Dados Pessoais</div>
          <div
            class="py-6 w-full border border-primary flex flex-col gap-4 font-semibold text-xs text-left px-3 md:px-10"
          >
            <div>
              <div class="mb-1">Nome:</div>
              <div>
                {{ form.nomeCompleto }}
              </div>
            </div>
            <div>
              <div class="mb-1">Endereço:</div>
              <div>
                {{ form.endereco }}
              </div>
            </div>
            <div>
              <div class="mb-1">E-mail</div>
              <div>
                {{ form.email }}
              </div>
            </div>
            <div>
              <div class="mb-1">CEP:</div>
              <div>{{ form.cep }}</div>
            </div>
            <div>
              <div class="mb-1">Celular:</div>
              <div>(11) 00000-0000</div>
            </div>
            <div>
              <div class="mb-1">Compl.:</div>
              <div>{{ form.complemento }}</div>
            </div>
            <div>
              <div class="mb-1">Tel. fixo:</div>
              <div>(11) 0000-0000</div>
            </div>
            <div>
              <div class="mb-1">Data nascimento:</div>
              <div>{{ form.dataNascimento }}</div>
            </div>
            <div>
              <div class="mb-1">CPF:</div>
              <div>{{ form.cpf }}</div>
            </div>
          </div>
          <div class="text-xs mb-2 mt-6">Dados de Recebimento</div>
          <div
            class="py-6 w-full border border-primary flex flex-col gap-4 font-semibold text-xs text-left px-3 md:px-10"
          >
            <div class="flex gap-x-2">
              <div>Banco:</div>
              <div>
                {{ form.banco }}
              </div>
            </div>
            <div class="flex gap-x-2">
              <div>Agencia:</div>
              <div>
                {{ form.agencia }}
              </div>
            </div>
            <div class="flex gap-x-2">
              <div>Conta</div>
              <div>
                {{ form.conta }}
              </div>
            </div>
            <div class="flex gap-x-2">
              <div>Tipo:</div>
              <div>{{ 'conta corrente' }}</div>
            </div>
            <div>
              <div>PIX:</div>
              <div>{{ form.pix }}</div>
            </div>
          </div>
          <div class="text-xs mb-2 mt-6">Dados dos Programas de Fidelidade</div>
          <div
            class="py-6 w-full border border-primary grid grid-cols-2 md:flex gap-4 px-3 md:px-10 justify-between mb-3"
            v-for="(selectedCia, i) in form.selectedCias"
            :key="i"
          >
            <div class="text-xs md:text-sm">
              <div class="font-semibold mb-5">Cia Aérea</div>
              <div class="text-xs">
                {{ selectedCia.label }}
              </div>
            </div>
            <div class="text-xs md:text-sm">
              <div class="font-semibold mb-5">Fidelidade</div>
              <div class="text-xs">
                {{ selectedCia.fidelidade }}
              </div>
            </div>
            <div class="text-xs md:text-sm">
              <div class="font-semibold mb-5">Senha</div>
              <div class="text-xs">
                {{ selectedCia.senhaAcesso }}
              </div>
            </div>
            <div class="text-xs md:text-sm">
              <div class="font-semibold mb-5">Limites CPF</div>
              <div class="text-xs">
                {{ selectedCia.qtdCpfs }}
              </div>
            </div>
          </div>
          <div class="text-xs text-gray-600 mt-8 pb-3">
            <div class="flex items-center">
              <input type="radio" class="h-5 w-5 mr-3" name="" />
              <div>
                Aceito os Termos e Condições de Uso e autorizo o uso dos meus dados de acordo com a
                Política de Privacidade
              </div>
            </div>
            <div class="flex items-center mt-5">
              <input type="radio" class="h-5 w-5 mr-3" name="" />
              <div>
                Aceito receber informações sobre as novidades e promoções dos serviços Turisky
              </div>
            </div>
          </div>
        </div>
        <div class="flex justify-end w-full mt-6">
          <div
            class="border-gray-700 border text-gray-700 text-center cursor-pointer w-44 mr-6 font-bold py-4 rounded-lg"
            @click="emit('finish')"
          >
            Acessar conta
          </div>
          <div
            class="bg-primary text-center text-white cursor-pointer w-44 font-bold py-4 rounded-lg"
            @click="emit('finish')"
          >
            Finalizar
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
defineProps(['form'])
const emit = defineEmits(['finish'])
function numberToBrl(value: number) {
  return value.toLocaleString('pt-br', { style: 'currency', currency: 'BRL' })
}
</script>
