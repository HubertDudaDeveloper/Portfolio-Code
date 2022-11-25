<template>
    <nav class="main__nav col-2 vh-100 d-md-flex flex-column gap-5">
        <img src="@/assets/logo_low.png" class="col-12"/>
        <strong>
            <ul class="main__nav-list col-12 d-flex flex-column gap-5">
                <ButtonComponent
                    v-for="(item, index) in props.navComponent"
                    :key="index"
                    class="text-white"
                    :customStyle="item.style"
                    :customClass="item.class"
                    :label="item.label"
                    :disabled="item.disabled"
                />
            </ul>
        </strong>
    </nav>
</template>
<script setup lang="ts">
import ButtonComponent from './ButtonComponent.vue'
import { defineProps } from 'vue'

const props = defineProps({
  navComponent: Array
})

</script>
