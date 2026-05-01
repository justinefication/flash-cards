<script lang="ts" setup>
import {cn} from "@/lib/utils.ts";
import {computed, ref} from "vue";

const flipped = ref(false);
const cursor = computed(() => flipped.value ? 'cursor-default' : 'cursor-help');
const helpText = computed(() => flipped.value ? 'See the question' : 'Show the answer')
</script>

<template>
    <main class="flex-1 border-t border-neutral-200">
        <div
            :class="cn(
                'relative container mx-auto border-x border-dashed border-neutral-200 h-full group group/scene',
                cursor
            )"
        >

            <div class="h-full perspective-distant">
                <div
                    :class="cn('relative transform-3d transition-transform duration-700 ease-out h-full', flipped && 'rotate-y-180')">

                    <slot/>

                </div>
            </div>

            <button
                class="absolute left-1/2 -translate-x-1/2 shadow-xs py-1.5 px-3 text-sm rounded-full bg-white backdrop-blur-3xl border border-neutral-200/80 opacity-0 -translate-y-10 group-hover/scene:-translate-y-20 group-hover/scene:opacity-85 transition-all duration-700 ease-in-out cursor-pointer"
                @click="flipped = !flipped"
            >
                {{ helpText }}
            </button>

            <div aria-hidden="true" class="size-2 bg-neutral-700 absolute -top-1 -left-1"></div>
            <div aria-hidden="true" class="size-2 bg-neutral-700 absolute -top-1 -right-1"></div>
        </div>
    </main>
</template>
