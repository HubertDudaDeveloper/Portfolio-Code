<template>
    <div class="position-relative vh-100 col-12">
    <section
          v-for="(item, index) in heroComponent"
          :key="'hero_' + index"
          class="hero-wrapper mb-5 vh-100 col-12 position-absolute"
          :id="'hero_' + index"
          >
          <Transition name="fade">
        <div class="hero d-grid"
            v-if="counterk('check') === index"
        >
            <img :src="item.img" class="col-12"/>
            <div class="shadow col-12"></div>
            <section class="hero__container col-12 d-flex flex-column flex-sm-row justify-content-evenly justify-content-sm-between align-items-center row" >
                <div class="col-2"></div>
                <section class="col-6 d-flex flex-column align-items-center text-white">
                    <h2 class="display-3">
                        {{item.title}}
                    </h2>
                    <p class="display-5">
                        {{item.p}}
                    </p>
                    <ButtonComponent
                        :label="''"
                        :customClass="`hero_btn ${item.button.class}`"
                    />
                </section>
                <section class="col-4 d-flex gap-sm-1 gap-5 flex-row-reverse flex-sm-column justify-content-center align-items-center text-white">
                    <ButtonComponent
                        :customClass="item.nav.front"
                        @click="counterk('inc')"
                    />
                    <ButtonComponent
                        :customClass="item.nav.back"
                        @click="counterk('dec')"
                    />
                </section>
            </section>
        </div>
        </Transition>
        </section>
    </div>
</template>
<script setup lang="ts">
import { defineProps, ref, reactive } from 'vue'
import ButtonComponent from './ButtonComponent.vue'
import { BIconArrowUp } from 'bootstrap-vue'
import { computed } from '@vue/reactivity'

const props = defineProps({
  heroComponent: Array
})

const state = reactive({
  ...props.heroComponent
})

// eslint-disable-next-line
let counter = ref(Number(0))
const counterk = (k) => {
  switch (k) {
    case 'inc':
      counter.value++
      counter.value = counter.value % props.heroComponent.length
      break
    case 'dec':
      counter.value--
      if (counter.value < 0) {
        counter.value = props.heroComponent.length - 1
      }
      break
    case 'check':
      return counter.value
  }
}

(async () => {
  await state
  console.log(state)
})()

</script>
