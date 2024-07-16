<script setup lang="ts">
import { ref } from 'vue';
import TextInput from './components/TextInput.vue';
import WButton from './components/WButton.vue';
const teste = ref('')
//
</script>

<template>
  <TextInput v-model="teste" label="TESTE" />
  <WButton active color="secondary" label="Btn 1" />
  <WButton active color="primary" label="Btn 2" />
</template>