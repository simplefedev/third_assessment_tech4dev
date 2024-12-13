<script>
export default {
    props: ['data'],
    computed: {
        classes() {
            return `event-card bg-cover rounded-xl flex justify-center items-center bg-[url(../views/assets/${[this.data.img]})] bg-blend-multiply hover:bg-black/60 transition-colors duration-500 bg-black/80 w-full min-w-[321px] h-[240px]`
        }
    }
}
</script>

<template>
    <div
        :class="classes">
        <p class="font-semibold text-2xl text-white">{{ data.caption }}</p>
    </div>
</template>