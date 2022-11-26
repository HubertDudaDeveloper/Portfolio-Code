<template>
  <section class="home">
    <MainNavComponent
      :navComponent="navComponent"
    />
    <HeroComponent
      :heroComponent="heroComponent"
    />
    <section class="d-flex flex-sm-row flex-column justify-content-center align-items-center text-white vh-100">
      <div class="col-2"></div>
      <article class="col-4 p-5">
        <h2>Technologie</h2>
        <p><em>aspiu efyroieuwar fasliku dfhoaiu hewfaerfi ousahdbfo viubhu asphoidujv piasdujfho apisufh oliasudFHO IUQYEW OIASDGHFVO IUASYDpaius fghi</em></p>
      </article>
      <div class="col-6 p-5">
        <HexagonComponent
          class="mb-5 d-flex justify-content-center align-items-center"
        />
      </div>
    </section>
    <section class="d-flex flex-sm-row flex-column justify-content-center align-items-center text-white vh-100">
      <FormComponent
        v-for="(item, index) in formComponent"
        :key="index"
        :label="item.label"
        :inputs="item.inputs"
        :selects="item.selects"
        :buttons="item.buttons"
        :consent="item.consent"
        :id="'form_' + index"
        class="text-white glass vh-50 pt-5 pb-5 col-7 rounded-5"
      />
    </section>
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
import heroComponent from '@/structure/dataHeroComponent.json'

</script>
