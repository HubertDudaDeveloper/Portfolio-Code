<template>
    <label :for="id" :required="required" :class="label.class">{{label.content}}</label>
    <select :class="customClass" :name="label"  :id="id" v-model="select.value" :required="required">
        <option v-for="(item, index) in props.option" :key="index" :value="item.value">{{item.value}}</option>
    </select>
</template>
<script setup lang="ts">
import { defineProps, ref } from 'vue'

const props = defineProps({
  function: String,
  customStyle: String,
  customClass: String,
  label: Object,
  required: Boolean,
  type: String,
  option: Array,
  id: String
})

const select = ref('')

</script>
