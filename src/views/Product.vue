<script>
import Button from '@/components/Button.vue';

export default {
    components: {
        Button,
    },
    data: function () {
        return {
            fetching: true,
            product: null,
        }
    },
    methods: {
        getProductById(id) {
            this.axios.get(`https://fakestoreapi.com/products/${id}`).then((response) => {
                this.fetching = false;
                console.log(response.data)
                this.product = response.data;
            })
        }
    },
    mounted() {
        this.getProductById(this.$route.query.id)
    }
};
</script>

<template>
    <main v-if="product" id="product" class="pt-36 px-6 lg:px-16 pb-24">
        <div class="flex flex-col gap-8">
            <div class="w-full group h-[360px] md:h-[480px] rounded-[10px]">
                <div :style="{ backgroundImage: `url('${product.image}')` }" id="product-photo"
                    class="w-full transition-transform duration-1000 group-hover: group-hover:scale-75 bg-no-repeat bg-center bg-contain hover:scale[.8] h-full rounded-[10px]">
                </div>
            </div>
            <div class="flex flex-col gap-2">
                <div id="ratings" class="flex gap-4 justify-center items-center">
                    <svg v-for="i of Array.from({length: 5}, (_, v) => v)" key="v" xmlns="http://www.w3.org/2000/svg" class="w-6 aspect-square" viewBox="0 0 30 30">
                        <path :class="`${i + 1 <= product.rating.rate ? 'drop-shadow-lg fill-[#783EAD]' : 'fill-black'}`"
                            d="M15.765,2.434l2.875,8.512l8.983,0.104c0.773,0.009,1.093,0.994,0.473,1.455l-7.207,5.364l2.677,8.576 c0.23,0.738-0.607,1.346-1.238,0.899L15,22.147l-7.329,5.196c-0.63,0.447-1.468-0.162-1.238-0.899l2.677-8.576l-7.207-5.364 c-0.62-0.461-0.3-1.446,0.473-1.455l8.983-0.104l2.875-8.512C14.482,1.701,15.518,1.701,15.765,2.434z"
                             />
                    </svg>
                </div>
                <div id="ratings-meta" class="text-sm flex justify-center">
                    <span class="font-medium">{{ `${product.rating.rate} / 5 of ${product.rating.count} total ratings`
                        }}</span>
                </div>
            </div>
            <div>
                <div class="flex flex-col gap-4">
                    <div class="flex justify-between font-bold text-[#432361]">
                        <span id="title">{{ product.title }}</span>
                        <span id="price">{{ product.price }}</span>
                    </div>
                    <div class="flex flex-col md:flex-row justify-between gap-8">
                        <div class="product-metadata flex flex-col gap-8 md:w-[55%]">
                            <div class="flex flex-col gap-2">
                                <div class="flex flex-col md:flex-row gap-2 md:gap-4">
                                    <span class="flex gap-1 items-center">
                                        <img src="./assets/calendar.svg" />
                                        <span>Sunday, October 3rd, 2023</span>
                                    </span>
                                    <span class="flex gap-1 items-center">
                                        <img src="./assets/time.svg" />
                                        <span>6PM</span>
                                    </span>
                                </div>
                                <span>
                                    <span class="flex gap-1 items-start md:items-center">
                                        <img src="./assets/Location.svg" />
                                        <span>Race Course, 8/9 Marina, Onikan, Lagos Lagos, 4aa Force
                                            Rd, Lagos Island 102273, Lagos</span>
                                    </span>
                                </span>
                                <span>
                                    <span class="flex gap-1 items-center">
                                        <img src="./assets/User.svg" />
                                        <span>RFK Junior</span>
                                    </span>
                                </span>
                            </div>
                            <div class="flex flex-col gap-4">
                                <p class="font-bold">
                                    Product description - (<span class="tex-xs text-[#783EAD]" id="category">{{ product.category.toUpperCase() }}</span>)
                                </p>
                                <p id="description">{{ product.description }}</p>
                                <p class="font-bold">Ticket Pricing</p>
                                <div class="flex gap-8">
                                    <p class="flex flex-col">
                                        <span class="font-medium">Single</span>
                                        <span id="single" class="text-[#9B51E0] font-bold">NGN {{ product.price }}</span>
                                    </p>
                                    <p class="flex flex-col">
                                        <span class="font-medium">Pair</span>
                                        <span id="pair" class="text-[#9B51E0] font-bold">NGN {{ product.price * 2 }}</span>
                                    </p>
                                </div>
                            </div>
                            <Button label="Buy now" classes="bg-[#783EAD]" />
                        </div>

                        <div class="contact-organisers flex flex-col gap-8 md:w-[40%]">
                            <div class="flex flex-col gap-2 md:gap-4">
                                <p class="font-bold">Contact Organisers</p>
                                <div class="flex gap-4">
                                    <img src="./assets/🦆 icon _circle email_.svg" />
                                    <img src="./assets/🦆 icon _rounded twitterbird_.svg" />
                                    <img src="./assets/ig.svg" />
                                </div>
                            </div>
                            <div class="flex flex-col gap-4">
                                <p class="font-bold">Directions</p>
                                <img src="./assets/map.png" />
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </main>
</template>
