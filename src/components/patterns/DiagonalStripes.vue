<script lang="ts" setup>
import {useId} from 'vue';

type DiagonalStripesProps = {
    asProgress?: boolean
}
const props = withDefaults(defineProps<DiagonalStripesProps>(), {
    asProgress: false
});

const patternId = `pattern-${useId()}`;
</script>
<template>
    <svg
        class="size-full stroke-zinc-300"
        fill="none"
    >
        <defs>
            <pattern
                :id="patternId"
                :class="props.asProgress ? 'animate-progress will-change-transform' : null"
                height="8"
                patternUnits="userSpaceOnUse"
                width="8"
                x="0"
                y="0"
            >
                <path d="M-1 5L5 -1M3 9L8.5 3.5" stroke-width="2"></path>
            </pattern>
        </defs>
        <rect :fill="`url(#${patternId})`" height="100%" stroke="none" width="100%"></rect>
    </svg>
</template>
