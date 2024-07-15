<script setup lang="ts">
withDefaults(
  defineProps<{
    label: string;
    labelAlt?: string;
    placeholder?: string;
    hideBottom?: boolean;
  }>(),
  {
    hideBottom: true,
  },
)

const modelValue = defineModel<string>({
  required: true,
})
</script>
<template>
  <label class="label">
    <span class="label-text">{{ label }}</span>
    <span v-if="labelAlt" class="label-text-alt">{{ labelAlt }}</span>
  </label>

  <input
    v-model="modelValue"
    aria-label="Input example"
    :placeholder="placeholder"
    class="input input-bordered w-full focus:outline-offset-0"
  />

  <label v-if="!hideBottom" class="label">
    <span class="label-text-alt">* Obrigatório</span>
    <span class="label-text-alt">0/20</span>
  </label>
</template>
