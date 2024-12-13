<script>
import Header from '@/components/Header.vue';
import Event from '@/components/Event.vue';
import Button from '@/components/Button.vue';
import ProductCard from '@/components/ProductCard.vue';

export default {
    components: {
        Header,
        Event,
        Button,
        ProductCard,
    },
    data: function () {
        return {
            fetching: true,
            products: null,
        }
    },
    methods: {
        getProducts() {
            this.axios.get('https://fakestoreapi.com/products').then((response) => {
                this.fetching = false;
                console.log(response.data)
                this.products = response.data;
            })
        }
    },
    mounted() {
        this.getProducts()
    }
};
</script>

<template>
    <section
        class="banner flex flex-col justify-between h-[640px] px-6 lg:px-16 py-[50px] bg-[url(../views/assets/banner.png)] bg-black/40 bg-blend-multiply bg-no-repeat bg-center bg-cover">
        <div class="flex flex-col lg:flex-row gap-4 mt-auto justify-between text-white">
            <p class="max-w-[460px] text-xl md:text-3xl font-bold">
                Ready to Rock? Discover the Hottest Events Here - Your Calendar's New
                Best Friend!
            </p>
            <form
                class="flex flex-col lg:flex-row gap-4 px-4 py-4 lg:py-0 lg:h-[100px] justify-center lg:items-center bg-white rounded-[20px]">
                <label
                    class="flex gap-2 w-full order-3 md:order-1 px-2 outline outline-1 lg:outline-none outline-[#E0E0E0] rounded">
                    <svg class="w-3 aspect-square" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 50 50">
                        <path class="fill-[#4F4F4F]"
                            d="M21 3C11.601563 3 4 10.601563 4 20C4 29.398438 11.601563 37 21 37C24.355469 37 27.460938 36.015625 30.09375 34.34375L42.375 46.625L46.625 42.375L34.5 30.28125C36.679688 27.421875 38 23.878906 38 20C38 10.601563 30.398438 3 21 3 Z M 21 7C28.199219 7 34 12.800781 34 20C34 27.199219 28.199219 33 21 33C13.800781 33 8 27.199219 8 20C8 12.800781 13.800781 7 21 7Z"
                            fill="#FFFFFF" />
                    </svg>
                    <input class="grow p-4 text-[#4F4F4F] border-none focus-visible:outline-none" type="text"
                        placeholder="Search for an event" />
                </label>
                <span class="order-2 w-full lg:w-1 h-px lg:h-[50%] bg-[#E0E0E0]"></span>
                <div class="flex justify-between order-1 md:order-3 lg:gap-6">
                    <select class="pr-12 bg-transparent text-[#4F4F4F]">
                        <option>Categories</option>
                    </select>
                    <button class="px-6 py-3 bg-[#783EAD] text-white rounded-[10px] hover:bg-black transition-colors">
                        Search
                    </button>
                </div>
            </form>
        </div>
    </section>
    <main class="px-6 lg:px-16 py-12">
        <div class="flex justify-between items-center font-semibold">
            <h2 class="text-sm">Trending events</h2>
            <p class="flex gap-1 text-xs text-[#432361]">
                <span>View all trending events</span>
                <svg class="w-3 aspect-square" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 32 32">
                    <path class="fill-[#432361]"
                        d="M13 6L13 8L22.5625 8L6.28125 24.28125L7.71875 25.71875L24 9.4375L24 19L26 19L26 6Z"
                        fill="#FFFFFF" />
                </svg>
            </p>
        </div>
        <section class="flex flex-col items-center md:grid md:grid-cols-2 lg:grid-cols-3 justify-center gap-6 py-12"
            id="cards">
            <div v-show="fetching" class="flex grow w-full">
                <ProductCard :product="null" />
            </div>
	    <div v-show="fetching" class="hidden md:block">
                <ProductCard :product="null" />
            </div>
	    <div v-show="fetching" class="hidden lg:block">
                <ProductCard :product="null" />
            </div>
            <div v-show="!fetching" v-for="product in products">
                <ProductCard :product="product" />
            </div>
        </section>
        <section
            class="flex flex-col justify-center my-24 pt-36 lg:justify-between lg:flex-row gap-4 lg:gap-24 lg:items-start">
            <div class="flex flex-col gap-6 lg:max-w-[393px]">
                <p class="font-semibold text-3xl md:max-[393px]">
                    Discover a World of Events Tailored Just for You.
                </p>
                <Button label="View all events" />
            </div>
            <div class="flex flex-col w-full gap-6 xl:grid grid-cols-2"
                v-for="item in [{ caption: 'Online Events', img: 'rect1.png' }, { caption: 'Physical Events', img: 'rect2.png' }, { caption: 'Hybrid Events', img: 'rect3.png' }]">
                <Event :key="item.caption" :data="item" />
            </div>
        </section>
    </main>
</template>
