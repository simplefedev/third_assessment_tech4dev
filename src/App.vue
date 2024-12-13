<script>
import { RouterLink, RouterView } from 'vue-router'
import Header from '@/components/Header.vue';


export default {
  components: {
    Header,
  },
}
</script>

<template>
  <Header />
  <RouterView />
  <footer class="md:flex-row flex flex-col gap-8 min-h-[343px] bg-[#432361] px-6 py-12 text-white justify-between">
    <div class="flex flex-col gap-4 max-w-xs">
      <h1 class="font-bold text-3xl">rendezvous</h1>
      <p>Your Personal Event Sherpa: Curating Awesome, One Click at a Time.</p>
    </div>
    <div class="flex flex-col font-semibold gap-4 lg:flex-row lg:gap-24">
      <div class="flex flex-col gap-2">
        <p class="font-bold text-xl">Feature</p>
        <ul class="flex flex-col">
          <li>Events discovery</li>
          <li>Ticketing</li>
        </ul>
      </div>
      <div class="flex flex-col gap-2">
        <p class="font-bold text-xl">Company</p>
        <ul class="flex flex-col">
          <li>About us</li>
          <li>FAQs</li>
          <li>Carees</li>
          <li>Support</li>
        </ul>
      </div>
      <div class="flex flex-col gap-2">
        <p class="font-bold text-xl">Contact us</p>
        <ul class="flex flex-col">
          <li>info@events.com</li>
          <li>+234 701 345 6789</li>
          <li>Race Course, /9 Marina,
            Onikan, Lagos Lagos. 4a Force Rd, Lagos Island 102273, Lagos
          </li>
        </ul>
      </div>
    </div>
  </footer>
</template>
