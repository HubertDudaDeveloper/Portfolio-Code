<template>
  <section class="home">
    <MainNavComponent
      :navComponent="navComponent"
    />
    <HeroComponent
      :heroComponent="heroComponent"
    />
    <section id="hexagon" class="hexagon position-relative d-flex flex-sm-row flex-column justify-content-center align-items-center text-white vh-100">
      <div class="col-2 p-5 p-sm-0"></div>
      <article class="col-sm-4 col-12 p-5 ">
        <h2>Technologie</h2>
        <p><em>aspiu efyroieuwar fasliku dfhoaiu hewfaerfi ousahdbfo viubhu asphoidujv piasdujfho apisufh oliasudFHO IUQYEW OIASDGHFVO IUASYDpaius fghi</em></p>
      </article>
      <div class="col-sm-6 col-12 p-sm-5">
        <HexagonComponent
          class="mb-5 d-flex justify-content-center align-items-center"
        />
      </div>
    </section>
    <section class="d-flex flex-sm-row flex-column justify-content-center align-items-start text-white vh-100">
      <div class="col-2"></div>
      <article class="col-sm-4 col-12 p-5">
        <h2>
          <strong>
            Formularz Kontaktowy
          </strong>
        </h2>
        <p>ijhasodifjh</p>
      </article>
      <div class="col-sm-6 col-12">
        <FormComponent
          v-for="(item, index) in formComponent"
          :key="index"
          :inputs="item.inputs"
          :selects="item.selects"
          :buttons="item.buttons"
          :consent="item.consent"
          :id="'form_' + index"
          class="text-white glass vh-50 pt-5 pb-5 col-sm-6 col-12 p-5 rounded-5"
        />
      </div>
    </section>
    <footer>
    <WavesComponent
      v-for="(item, index) in wavesComponent"
      :key="index"
      :color="item.color"
      :directiong="item.direction"
      :id="'waves_' + index"
    />
      <div class="footer d-flex justify-content-center align-items-center flex-column gap-5 pb-5 text-white">
        <strong class="footer d-flex justify-content-center align-items-center flex-sm-row flex-column gap-5">
          <ul class="d-flex justify-content-center flex-column">
            <h3 class="align-self-center">Kontakt:</h3>
            <li>Email: <a href="mailto:kontakt@hd-dev.pl">kontakt@hd-dev.pl</a></li>
            <li>Tel: <a href="tel:+48555555555">555-555-555</a></li>
            <li>Linkedin: <a href="">Link</a></li>
          </ul>
          <ul class="d-flex justify-content-center flex-column">
            <h3 class="align-self-center">Site map:</h3>
            <li>O Nas</li>
            <li>Techstack</li>
            <li>Regulamin</li>
          </ul>
        </strong>
        <h4>Author<strong> Hubert Duda</strong></h4>
      </div>
  </footer>
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
import { createElementVNode } from 'vue'

const background = () => {
  setTimeout(() => {
    for (let k = 0; k <= 50; k++) {
      const waves = document.querySelectorAll('.hexagon')
      console.log(waves)
      waves.forEach((item) => {
        const container = document.createElement('div')
        container.classList.add('position-absolute')
        container.classList.add('d-flex')
        container.classList.add('col-12')
        container.classList.add('justify-content-evenly')
        container.style.top = k * 50 + 'px'
        container.style.zIndex = '-1'
        for (let i = 0; i <= 25; i++) {
          const bg = document.createElement('i')
          bg.classList.add('bi-code-slash')
          bg.classList.add('bi')
          bg.classList.add('icon-animate')
          bg.style.fontSize = '1.2rem'
          bg.style.zIndex = '0'
          bg.style.color = '#b2fcfb'
          bg.style.opacity = '0.2'
          container.appendChild(bg)
        }
        item.appendChild(container)
      })
    }
  }, 500)
}
background()
</script>
