<script lang="ts" setup>
</script>
<template>
    <footer class="h-36 lg:h-48 border-t border-neutral-200">
        <div class="relative container mx-auto p-4 h-full border-x border-neutral-200">

            <div class="flex flex-row gap-2">
                <slot/>
            </div>

            <div aria-hidden="true" class="size-2 bg-neutral-700 absolute -top-1 -left-1"></div>
            <div aria-hidden="true" class="size-2 bg-neutral-700 absolute -top-1 -right-1"></div>
        </div>
    </footer>
</template>
