<script lang="ts" setup>
import {computed} from "vue";
import DiagonalStripes from "@/components/patterns/DiagonalStripes.vue";

type ProgressIndicatorProps = {
    progress: number;
    max: number;
    showIndicator?: boolean;
}
const props = withDefaults(defineProps<ProgressIndicatorProps>(), {
    showIndicator: false,
});
const currentProgressPercentage = computed(() => Math.round((props.progress / props.max) * 100))
</script>

<template>
    <div :style="{ width: currentProgressPercentage + '%' }"
         class="h-6 relative flex items-center gap-2 transition-[width] duration-700 ease-out">
        <DiagonalStripes asProgress/>

        <span v-if="props.showIndicator"
              class="text-neutral-700 tracking-wider animate-pulse"
        >
            {{ currentProgressPercentage }}%
        </span>
    </div>
</template>
