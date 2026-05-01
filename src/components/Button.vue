<script lang="ts" setup>
import {cn} from '@/lib/utils';
import type {HTMLAttributes} from "vue";

type ButtonProps = {
    class?: HTMLAttributes['class']
}

const props = defineProps<ButtonProps>();
</script>
<template>
    <button
        :class="cn('p-4 border flex flex-row gap-3',
            'items-center justify-center',
            'text-sm tracking-widest',
            'border-zinc-300 hover:bg-zinc-900 hover:text-zinc-100 hover:fill-zinc-100',
            'transition-colors duration-300 ease-in-out',
            props.class)"
    >
        <slot/>
    </button>
</template>
