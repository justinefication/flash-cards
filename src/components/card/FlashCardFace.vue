<script lang="ts" setup>
import {cn} from "@/lib/utils.ts";
import External from "@/components/icons/External.vue";

type FlashCardFaceProps = {
    heading: string;
    content?: string;
    link?: string;
    side?: 'front' | 'back';
}
const props = withDefaults(defineProps<FlashCardFaceProps>(), {
    side: 'front'
});
</script>

<template>
    <div
        :class="cn(
            'absolute inset-0 flex flex-col items-center justify-center backface-hidden gap-8 px-2 lg:px-40',
            {
                'rotate-y-180 bg-white': side === 'back'
            }
        )"
    >

        <h1 class="font-heading text-4xl lg:text-6xl tracking-tight text-neutral-800">{{ props.heading }}</h1>

        <p class="font-features-['ss01','ss04'] font-sans text-lg lg:text-3xl leading-8 lg:leading-10 text-center text-neutral-600">
            {{ props.content }}
        </p>

        <a v-if="link && link.trim().length > 0"
           :href="link"
           aria-description="Opens in another tab"
           class="text-neutral-600 hover:text-neutral-950 text-sm flex gap-2 items-center group/link transition-colors duration-200 ease-in"
           rel="noopener noreferrer"
           target="_blank"
        >
            LEARN MORE
            <External class="size-4 -mt-0.5 fill-neutral-600 group-hover/link:fill-neutral-950"/>
        </a>
    </div>
</template>
