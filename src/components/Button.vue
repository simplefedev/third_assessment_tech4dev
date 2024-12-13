<script>
    export default {
        props: {
            label: {
                type: String,
                required: true
            },
            classes: {
                type: String,
                default: 'bg-[#432361]'
            }
        }
    }
</script>

<template>
    <a
            href="#"
            class="self-start hover:bg-black transition-colors text-white font-semibold p-3 px-6 rounded-[10px]"
            :class="classes"
            >{{ label }}</a
          >
</template>