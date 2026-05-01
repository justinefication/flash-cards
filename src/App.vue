<script lang="ts" setup>
import SkipBack from "@/components/icons/SkipBack.vue";
import Button from "@/components/Button.vue";
import ProgressIndicator from "@/components/ProgressIndicator.vue";
import {CardContent, CardFace, CardFooter, CardHeader, FlashCard} from "@/components/card";
import SkipForward from "@/components/icons/SkipForward.vue";
import DiagonalStripes from "@/components/patterns/DiagonalStripes.vue";
import {ref} from "vue";
import flashCardData from '@/data/data.json';

const flashCardIndex = ref(0);
const flashCardCount = flashCardData?.length;

const previous = () => {
    if (flashCardIndex.value === 0) {
        return
    }

    flashCardIndex.value--;
}

const next = () => {
    if (flashCardIndex.value === flashCardData.length - 1) {
        return;
    }

    flashCardIndex.value++;
}
</script>
<template>
    <FlashCard>
        <CardHeader>
            <p class="text-sm tracking-widest text-neutral-700">PROGRESS:</p>
            <ProgressIndicator :max="flashCardCount" :progress="flashCardIndex + 1" :show-indicator="true"/>
        </CardHeader>

        <CardContent>
            <CardFace
                :content="flashCardData[flashCardIndex]?.question"
                heading="Question"
            />

            <CardFace
                :content="flashCardData[flashCardIndex]?.answer"
                :link="flashCardData[flashCardIndex]?.link"
                heading="Answer"
                side="back"
            />
        </CardContent>

        <CardFooter>
            <Button class="w-80" @click="previous">
                <SkipBack class="size-4"/>
                PREVIOUS
            </Button>

            <DiagonalStripes class="h-13.5 hidden md:flex flex-1"/>

            <Button class="w-80" @click="next">
                NEXT
                <SkipForward class="size-4"/>
            </Button>
        </CardFooter>
    </FlashCard>
</template>
