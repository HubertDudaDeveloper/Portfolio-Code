<template>
  <div v-if="type !== 'textarea'" class="col-12">
    <label :for="id" :required="required" :class="label.class"><strong>{{ label.content }}</strong></label>
    <input :class="customClass" :placeholder="placeholder"  :id="id" :type="type" v-model="input.value" :required="required"/>
  </div>
  <div v-else class="col-12">
    <label :for="id" :required="required" :class="label.class"><strong>{{ label.content }}</strong></label>
    <textarea :class="customClass" :placeholder="placeholder"  :id="id" :type="type" v-model="input.value" :required="required"></textarea>
  </div>
</template>
<script setup lang="ts">
import { defineProps, ref } from 'vue'

const props = defineProps({
  function: String,
  customStyle: String,
  customClass: String,
  required: Boolean,
  label: Object,
  placeholder: String,
  type: String,
  id: String
})

const input = ref('')

</script>
