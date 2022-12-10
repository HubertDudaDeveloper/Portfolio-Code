<template>
    <nav id="main__nav" class="main__nav col-12 col-lg-1 col-xl-2 vh-25 d-flex justify-content-between justify-content-lg-start flex-row flex-lg-column gap-5">
        <img src="@/assets/logo_low.png" class=" col-lg-12 mt-2 mt-md-0"/>
            <ButtonComponent
                class="bi bi-list rounded-0 h-50 m-3 glass text-white d-lg-none d-flex align-self-center align-items-center rounded-2"
                :disabled="false"
            />
            <ul class="main__nav-list col-12 d-none d-lg-flex flex-sm-column gap-5 pt-5 pt-md-1">
                <ButtonComponent
                    v-for="(item, index) in props.navComponent"
                    :key="index"
                    class="text-white"
                    :customClass="item.class"
                    :label="item.label"
                    :disabled="item.disabled"
                />
                <ButtonComponent
                    class="text-white align-self-center"
                    :customClass="'glass p-3 bi bi-arrow-bar-left rounded-1'"
                    :disabled="false"
                    @click="resizeBar($event)"
                    v-show="screen"
                />
            </ul>
    </nav>
</template>
<script setup lang="ts">
import ButtonComponent from './ButtonComponent.vue'
import { defineProps, ref, computed } from 'vue'

const props = defineProps({
  navComponent: Array
})

const screen = computed(() => {
  return window.screen.width <= 1024
})

const resizeBar = (event) => {
  const nav = document.getElementById('main__nav')
  const before = document.querySelectorAll('span.d-none,d-lg-inline')

  if (event.target.style.rotate === '180deg') {
    event.target.style.rotate = '0deg'
  } else {
    event.target.style.rotate = '180deg'
  }

  nav.classList.toggle('col-lg-2')
  before.forEach((item) => {
    item.classList.toggle('d-lg-inline')
  })
}

</script>
