<template>
  <section class="home">
    <MainNavComponent
      :navComponent="navComponent"
    />
    <HeroComponent/>
    <HexagonComponent
    class="mb-5 vh-100 d-flex justify-content-center align-items-center"
    />
    <FormComponent
      v-for="(item, index) in formComponent"
      :key="index"
      :label="item.label"
      :inputs="item.inputs"
      :selects="item.selects"
      :buttons="item.buttons"
      :consent="item.consent"
      :id="'form_' + index"
      class="p-5 text-white"
    />
    <WavesComponent
      v-for="(item, index) in wavesComponent"
      :key="index"
      :color="item.color"
      :directiong="item.direction"
      :id="'waves_' + index"
    />
  </section>
</template>

<script setup lang="ts">
import FormComponent from '@/components/FormComponent.vue'
import HeroComponent from '@/components/HeroComponent.vue'
import HexagonComponent from '@/components/HexagonComponent.vue'
import MainNavComponent from '@/components/MainNavComponent.vue'
import WavesComponent from '@/components/WavesComponent.vue'

import formComponent from '@/structure/dataFormComponent.json'
import navComponent from '@/structure/dataMainNavComponent.json'
import wavesComponent from '@/structure/dataWavesComponent.json'

</script>
