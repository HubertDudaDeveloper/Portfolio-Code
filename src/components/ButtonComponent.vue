<template>
    <button :style="customStyle" :class="customClass" class="btn" v-if="true">
      <strong>
        <span v-if="props.customClass?.includes('bi')" class="d-none d-xl-inline">{{label}}</span><span v-else class="d-inline">{{label}}</span>
      </strong>
    </button>
</template>
<script setup lang="ts">
import { defineProps } from 'vue'

const props = defineProps({
  function: String,
  click: String,
  customStyle: String,
  customClass: String,
  label: String
})

</script>
