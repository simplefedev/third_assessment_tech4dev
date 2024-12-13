<script>
import Hamburger from '@/components/Hamburger.vue';

export default {
  data: function () {
    return {
      path: this.$route.fullPath
    }
  },
  components: {
    Hamburger,
  },
}
</script>

<template>
  <div
    class="absolute top-12 flex justify-between items-center w-full px-12 py-3 lg:bg-white/60 rounded-[20px] lg:backdrop-blur">
    <h1 v-show="$route.fullPath === '/'" class="text-[32px] text-white lg:text-[#432361] font-bold">
      rendezvous 
    </h1>
    <h1 v-show="$route.fullPath.includes('/product')" class="text-[32px] text-[#432361] font-bold">
      rendezvous 
    </h1>
    <nav ref="navRef" id="nav"
      class="nav fixed lg:static z-20 inset-0 bg-white/90 w-full flex lg:bg-transparent items-center h-full lg:h-auto py-20 lg:py-0 font-bold backdrop-blur -translate-y-full lg:translate-y-0 transition-transform">
      <ul
        class="flex text-[#432361]  relative lg:static top-12 md:top-0 -translate-y-full lg:translate-y-0 justify-center mx-auto w-full lg:w-auto flex-col items-center lg:flex-row gap-6 gap-2 p-2">
        <li class=""><a class="p-2 hover:text-[#783EAD] transition-colors" href="">Discover</a></li>
        <li><a class="p-2 hover:text-[#783EAD] transition-colors" href="">About us</a></li>
        <li><a class="p-2 hover:text-[#783EAD] transition-colors" href="">FAQs</a></li>
        <li><a class="p-2 hover:text-[#783EAD] transition-colors" href="">Contact us</a></li>
        <li class="lg:hidden"><a class="p-2 hover:text-[#783EAD] transition-colors" href="">Log in</a></li>
        <li class="lg:hidden">
          <a class="px-6 py-3 bg-[#783EAD] text-white rounded-[10px] hover:bg-black transition-colors" href="">Sign
            up</a>
        </li>
      </ul>
      <ul class="hidden lg:flex justify-center flex-col lg:flex-row gap-6 items-center gap-2 p-2">
        <li><a class="p-2 hover:text-[#783EAD] transition-colors" href="">Log in</a></li>
        <li>
          <a class="px-6 py-3 bg-[#783EAD] text-white rounded-[10px] hover:bg-black transition-colors" href="">Sign
            up</a>
        </li>
      </ul>
    </nav>
    <Hamburger :color="$route.fullPath" />
  </div>
</template>