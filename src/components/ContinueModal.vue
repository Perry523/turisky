<template>
  <Teleport to="#root" class="absolute">
    <div class="h-full w-screen bg-gray-700 opacity-50 absolute top-0"></div>
    <div class="w-screen flex top-1/4 justify-center fixed">
      <div class="w-10/12 md:w-auto px-4 md:px-28 py-5 md:py-10 rounded-lg bg-white">
        <div class="text-sm md:text-lg mb-5 text-center">
          Caso você ja tenha um cadastro, acesse sua conta para <br class="hidden md:block" />
          realizar sua venda. Se não, clique em continuar para realizar
          <br class="hidden md:block" />
          seu cadastro e finalizar sua venda.
        </div>
        <div class="flex justify-center mt-5">
          <div
            class="text-primary text-center text-sm border border-primary w-32 md:w-44 py-5 mr-4 cursor-pointer font-bold rounded-lg"
          >
            Acessar conta
          </div>
          <div
            class="bg-primary text-center text-sm text-white cursor-pointer font-bold rounded-lg w-32 md:w-44 py-5"
            @click="emit('continue')"
          >
            Continuar
          </div>
        </div>
      </div>
    </div>
  </Teleport>
</template>
<script setup lang="ts">
const emit = defineEmits(['continue'])
</script>
