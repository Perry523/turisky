<template>
  <div id="root" class="relative">
    <div class="bg-black h-24 w-full"></div>
    <div class="relative">
      <img src="@/assets/blog.png" class="w-full" alt="" />
      <div class="absolute font-bold h-full w-full top-0 flex flex-col justify-center">
        <div class="text-5xl md:text-[250px] text-white md:leading-[150px] text-center">Blog</div>
      </div>
    </div>

    <div class="w-full px-[5%] py-5 md:px-[9%] md:py-10" style="background: #f6f2e9">
      <div class="flex flex-col items-center mt-16">
        <div class="w-9/12 relative flex items-center">
          <MagnifyingGlassIcon class="absolute left-6 w-3 text-primary"></MagnifyingGlassIcon>
          <input
            type="text"
            class="w-full h-11 bg-[#D1CDC4] pl-14 focus:outline-none text-xs placeholder:text-gray-800 placeholder:text-xs text-gray-800 rounded-md"
            placeholder="Buscar artigos"
          />
          <div
            class="absolute right-2 text-xs font-semibold bg-primary text-center text-white cursor-pointer h-8 px-7 flex items-center rounded"
          >
            Buscar
          </div>
        </div>
        <div class="w-7/12 flex font-semibold mt-4 items-center">
          <div class="text-xs mr-1">Tags Populares:</div>
          <div class="flex gap-x-3">
            <div v-for="(tag, i) in tags" :key="i" class="bg-[#D1CDC4] text-xs py-1 px-3">
              {{ tag }}
            </div>
          </div>
        </div>
        <div class="w-full mt-24">
          <div class="flex justify-between items-center text-gray-800">
            <div class="text-2xl font-bold">Artigos Populares</div>
            <div class="border border-black rounded py-2 px-4 flex font-bold">
              <div class="text-xs mr-2">Ver Todos</div>
              <ArrowRightIcon class="w-3 text-primary" />
            </div>
          </div>
          <div class="grid grid-cols-3 gap-2 mt-10">
            <ArticleCard
              v-for="(artigo, i) in 3"
              :key="i"
              :author-name="'Rafael Silva'"
              :author-image="'src/assets/user.png'"
              :bg-image="'src/assets/artigos_populares.jfif'"
              :title="'Férias Merecida: Chegou a hora de viajar'"
              :date="'02/05/2024'"
              :badge="'destaque'"
              classes="h-96"
            ></ArticleCard>
          </div>
        </div>
        <div class="w-full mt-24">
          <div class="flex justify-between items-center text-gray-800">
            <div class="text-2xl font-bold">Artigos Recentes</div>
            <div class="border border-black rounded py-2 px-4 flex font-bold">
              <div class="text-xs mr-2">Ver Todos</div>
              <ArrowRightIcon class="w-3 text-primary" />
            </div>
          </div>
          <div class="grid grid-cols-4 gap-3 mt-10">
            <ArticleCard
              v-for="(artigo, i) in 4"
              :key="i"
              :author-name="'Lina Hicks'"
              :author-image="'src/assets/user.png'"
              :bg-image="'src/assets/artigos_recentes.jfif'"
              :title="'Compre Milhas'"
              :description="'Agora ficou fácil comprar e vender milhas'"
              :date="'02/05/2024'"
              classes="h-80"
            ></ArticleCard>
          </div>
        </div>
        <div class="w-full mt-24">
          <div class="flex justify-between items-center text-gray-800">
            <div class="text-2xl font-bold">Fique Ligado</div>
            <div class="border border-black rounded py-2 px-4 flex font-bold">
              <div class="text-xs mr-2">Ver Todos</div>
              <ArrowRightIcon class="w-3 text-primary" />
            </div>
          </div>
          <div class="grid grid-cols-2 gap-7 mt-10">
            <ArticleCard
              v-for="(artigo, i) in 2"
              :key="i"
              :author-name="'Lina Hicks'"
              :author-image="'src/assets/user.png'"
              :bg-image="'src/assets/fique_ligado.jfif'"
              :title="'Viagem a dois e com promoção no mês de Junho'"
              :date="'02/05/2024'"
              classes="h-[520px]"
            ></ArticleCard>
          </div>
          <div class="grid grid-cols-3 gap-7 mt-7">
            <ArticleCard
              v-for="(artigo, i) in 3"
              :key="i"
              :author-name="'Lina Hicks'"
              :author-image="'src/assets/user.png'"
              :bg-image="'src/assets/fique_ligado2.jfif'"
              :title="'Milhas em promoção'"
              :description="'O mês de Junho será de promoção. Milhas mais baratas'"
              :date="'02/05/2024'"
              classes="h-[430px]"
            ></ArticleCard>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script setup lang="ts">
import { ref } from 'vue'
import { MagnifyingGlassIcon, ArrowRightIcon } from '@heroicons/vue/24/solid'
import ArticleCard from '@/components/ArticleCard.vue'
const tags = ref(['Férias', 'Comprar milhas', 'Viagem a dois'])
</script>
<style>
.banner-height {
  height: calc(100vh - 96px);
}
</style>
