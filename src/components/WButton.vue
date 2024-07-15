<script setup lang="ts">
import { computed } from 'vue';

type ButtonColors = 'neutral' | 'primary' | 'secondary' | 'accent' | 'ghost' | 'link'

const props = withDefaults(
    defineProps<{
        active?: boolean,
        color?: ButtonColors
    }>(),
    {
        active: false,
        color: undefined
    }
)

const active = computed(() => props.active ? 'btn-active' : undefined)
const color = computed(() => {
    switch (props.color) {
        case 'accent':
            return 'btn-accent';
        case 'neutral':
            return 'btn-neutral';
        case 'primary':
            return 'btn-primary';
        case 'secondary':
            return 'btn-secondary';
        case 'ghost':
            return 'btn-ghost';
        case 'link':
            return 'btn-link';
        default: 
            return undefined
    }
})
</script>
<template>
    <button class="btn" :class="[
        active,
        color
    ]">
        Default
    </button>
</template>