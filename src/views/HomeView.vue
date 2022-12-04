<template>
  <section class="home">
    <MainNavComponent
      :navComponent="navComponent"
    />
    <HeroComponent
      :heroComponent="heroComponent"
    />
    <section id="hexagon" class="hexagon position-relative d-flex flex-lg-row flex-column justify-content-center align-items-center text-white vh-100">
      <div class="col-3 p-5 p-sm-0 d-none d-sm-block"></div>
      <article class="col-lg-3 col-12 p-5 h-50">
        <h2>Technologie</h2>
        <p><em>aspiu efyroieuwar fasliku dfhoaiu hewfaerfi ousahdbfo viubhu asphoidujv piasdujfho apisufh oliasudFHO IUQYEW OIASDGHFVO IUASYDpaius fghi</em></p>
      </article>
      <div class="col-sm-6 col-12 p-sm-5 h-50">
        <HexagonComponent
          class="mb-5 d-flex justify-content-center align-items-center"
        />
      </div>
    </section>
    <section class="form d-flex flex-sm-row flex-column justify-content-center align-items-center text-white vh-100">
      <div class="col-3"></div>
      <article class="glass col-sm-3 col-12 rounded-5 align-self-center mb-5 position-relative start-20 d-flex flex-column justify-content-center align-items-center">
        <h2 class="col-12 p-4">
          Tytuł artykuł!
        </h2>
        <p class="col-12 p-5">
          Wyślij nam wiadomość!
        </p>
        <div class="envelope col-9 d-flex flex-column gap-5 position-relative p-5 mb-5">
          <i class="bi bi-envelope-fill text-custom-primary display-1 position-absolute "></i>
          <i class="bi bi-envelope-open-fill text-custom-primary display-1 position-absolute "></i>
          <i class="bi bi-envelope-paper-fill text-custom-primary display-1 position-absolute"></i>
        </div>
      </article>
      <div class="col-sm-6 col-12">
        <FormComponent
          v-for="(item, index) in formComponent"
          :key="index"
          :label="item.label"
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
    const dencity = window.visualViewport.width / 75
    for (let k = 0; k <= 19; k++) {
      const waves = document.querySelectorAll('.hexagon')
      waves.forEach((item) => {
        const container = document.createElement('div')
        container.classList.add('position-absolute', 'd-flex', 'col-12', 'justify-content-center')
        container.style.cssText = `
          top: ${k * 5}vh;
          z-index= -1;
        `
        for (let i = 0; i <= dencity; i++) {
          const bg = document.createElement('i')
          bg.classList.add('d-flex', 'bi-code-slash', 'icon-animate', 'bi', 'justify-content-center', 'align-items-center')
          bg.id = `y${i}x${k}-item`
          container.appendChild(bg)
        }
        item.appendChild(container)
      })
    }
  }, 200)
}
background()

const randomId = () => {
  return new Promise((resolve, reject) => {
    const maxY = window.visualViewport.width / 75
    const maxX = 19
    const min = 0
    // eslint-disable-next-line
    let randomY = Math.floor(Math.random() * (maxY - min + 1) + min)
    // eslint-disable-next-line
    let randomX = Math.floor(Math.random() * (maxX - min + 1) + min)
    // eslint-disable-next-line
    let id = `y${Math.floor(randomY)}x${Math.floor(randomX)}-item`
    if (id !== undefined || id !== null) {
      resolve(id)
    } else {
      reject(id)
    }
  })
}
setInterval(() => {
  randomId()
    .then((res) => {
      if (res !== undefined || res !== null) {
        document.getElementById(res).style.cssText += 'opacity: 1; text-shadow: 0px 0px 20px #b2fcfb;'
        setTimeout(() => {
          document.getElementById(res).style.cssText += 'opacity: 0.1; text-shadow: none;'
        }, 1000)
      }
    })
    .catch((err) => {
      return err
    })
}, 200)
</script>
