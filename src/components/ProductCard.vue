<script>
import { RouterLink } from 'vue-router';

export default {
    props: ['product'],
}
</script>

<template>

    <article v-show="!product"
        class="grow animate-pulse bg-neutral-300 relative card flex group flex-col w-full max-w-[336px] md:min-w-[307px] md:max-w-xl border border-1 border-[#E0E0E0] rounded-lg shadow min-h-[514px]">
        <div class="card__thumbnail bg-black/20 h-[240px] bg-contain rounded-t-lg transition duration-10"></div>
        <div class="flex flex-col gap-6 px-6 py-8">
            <div class="metadata flex flex-col gap-2">
                <p class="title w-full h-3 rounded-full bg-neutral-400 font-semibold"></p>
                <span class="h-2 w-1/2 bg-neutral-400 rounded-full"></span>
                <div class="flex flex-col gap-4 mt-5">
                    <p class="title w-full h-3 rounded-full bg-neutral-400 font-semibold"></p>
                    <p class="title w-full h-3 rounded-full bg-neutral-400 font-semibold"></p>
                    <p class="title w-full h-3 rounded-full bg-neutral-400 font-semibold"></p>
                    <p class="title w-full h-3 rounded-full bg-neutral-400 font-semibold"></p>
                </div>
            </div>
            <span class="h-2 w-1/4 bg-neutral-400 rounded-full"></span>
        </div>
    </article>

    <article v-if="product"
        class="grow relative card flex group flex-col w-full max-w-[336px] md:min-w-[307px] md:max-w-xl border border-1 border-[#E0E0E0] rounded-lg shadow min-h-[514px]">
        <span
            class="bg-[#783EAD]/80 text-xs z-50 absolute top-4 text-white font-bold shadow right-2 px-4 py-2 rounded-full">{{
                product.category }}</span>
        <div class="card__thumbnail bg-black/20 group-hover:bg-black/0 bg-blend-multiply group-hover:scale-[.8] h-[240px] bg-contain bg-no-repeat bg-center rounded-t-lg transition duration-10"
            :style="{ backgroundImage: `url('${product.image}')` }">
        </div>
        <div class="flex flex-col gap-6 px-6 py-8">
            <div class="metadata flex flex-col gap-2">
                <p class="title font-semibold">{{ `${product.title.substring(0, 25)} ${product.title.length > 25 ? '...'
                    : ''}` }}</p>
                <p class="category-ratings font-medium text-xs flex gap-2">
                    <span class="category text-small">{{ product.category.toUpperCase() }}</span>
                    <span class="dot text-small text-[#432361]">●</span>
                    <span class="font-bold">{{ product.rating.rate + '/ 5: - ' + product.rating.count + ' ratings'
                        }}</span>
                </p>
            </div>
            <p class="description font-light">{{ `${product.description.substring(0, 160)} ${product.description.length
                > 160 ? '...' : ''}` }}</p>
            <RouterLink class="flex gap-1" :to="{ name: 'product', query: { id: product.id } }">
                <span class="text-[#432361] text-xs">View Details</span>
                <svg class="w-3 aspect-square" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 32 32" fill="#FFFFFF">
                    <path class="fill-[#432361]"
                        d="M13 6L13 8L22.5625 8L6.28125 24.28125L7.71875 25.71875L24 9.4375L24 19L26 19L26 6Z"
                        fill="#FFFFFF"></path>
                </svg>
            </RouterLink>
        </div>
    </article>

</template>