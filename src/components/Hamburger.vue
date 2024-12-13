<script>
export default {
    methods: {
        toggleMenu(event) {
            const nav = document.getElementById('nav');
            nav.classList.toggle('open');
        }
    },
    props: [ 'color' ],
};
</script>

<template>
    <button class="hamburger-container lg:hidden" @click="toggleMenu">
        <span v-show="color === '/'" id="hamburger" class="hamburger bg-white"></span>
        <span v-show="color.includes('/product')" id="hamburger" class="hamburger bg-[#432361]"></span>
    </button>
</template>

<style>
.nav.open {
    transform: translateY(0);
}

.nav.open+.hamburger-container .hamburger {
    background-color: transparent;
}

.nav.open+.hamburger-container .hamburger::before,
.nav.open+.hamburger-container .hamburger::after {
    background-color: #783EAD;
}

.nav.open+.hamburger-container .hamburger::before {
    top: 0;
    transform: rotate(45deg);
}

.nav.open+.hamburger-container .hamburger::after {
    bottom: 0;
    transform: rotate(-45deg);
}

.hamburger-container {
    position: relative;
    z-index: 999;
    height: calc((3px * 3) + (.5rem * 2));
}

.hamburger {
    position: relative;
    display: block;
    background-color: white;
    width: 2rem;
    height: 3px;
    border-radius: 999px;
    transition: all 700ms ease-in-out;
}

.product-hamburger {
    background-color: #432361;
    transition: all 300ms ease-in-out;
}

.hamburger::before,
.hamburger::after {
    content: '';
    position: absolute;
    height: inherit;
    width: inherit;
    background-color: inherit;
    left: 0;
    right: 0;
    border-radius: inherit;
}

.hamburger::before {
    top: -.5rem;
}

.hamburger::after {
    bottom: -.5rem;
}
</style>