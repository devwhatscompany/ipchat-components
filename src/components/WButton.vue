<script setup lang="ts">
import { computed } from 'vue'

type ButtonColors =
    | 'neutral'
    | 'primary'
    | 'secondary'
    | 'accent'
    | 'ghost'
    | 'link'
    | 'info'
    | 'success'
    | 'warning'
    | 'error'

type RenderAs = 'a' | 'input' | 'button';
type InputTypes = 'button' | 'submit' | 'radio' | 'checkbox' | 'reset'

const props = withDefaults(
    defineProps<{
        label?: string
        active?: boolean
        color?: ButtonColors
        disabled?: boolean;
        inputType?: InputTypes;
        as?: RenderAs;
    }>(),
    {
        as: 'button',
        inputType: 'button',
        active: false,
        color: undefined
    }
)

const active = computed(() => (props.active ? 'btn-active' : undefined))
const color = computed(() => {
    switch (props.color) {
        case 'accent':
            return 'btn-accent'
        case 'neutral':
            return 'btn-neutral'
        case 'primary':
            return 'btn-primary'
        case 'secondary':
            return 'btn-secondary'
        case 'ghost':
            return 'btn-ghost'
        case 'link':
            return 'btn-link'
        case 'info':
            return 'btn-info'
        case 'success':
            return 'btn-success'
        case 'warning':
            return 'btn-warning'
        case 'error':
            return 'btn-error'
        default:
            return undefined
    }
})

const cssClass = computed(() => [active.value, color.value])
</script>
<template>
    <template v-if="as === 'button'">
        <button class="btn" :class="cssClass" v-bind="$attrs" :aria-label="label">
            {{ label }}
        </button>
    </template>
    <template v-else-if="as === 'a'">
        <a role="button" class="btn" :class="cssClass" v-bind="$attrs" :aria-label="label">
            {{ label }}
        </a>
    </template>
    <template v-else-if="as === 'input'">
        <input class="btn" :class="cssClass" v-bind="$attrs" :aria-label="['button', 'submit', 'reset'].includes(inputType) ? undefined : label" />
    </template>
</template>
