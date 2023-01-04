<template>
    <div class="w-full max-w-4xl place-item-center p-8 flex-row flex-grow-0 bg-slate-200 h-screen space-y-4">
        <Header />
        <div class="border border-slate-50 shadow bg-white p-2 rounded-md h-48">{{ section }}</div>
    </div>
</template>

<script>
import Header from '/src/components/Header.vue';

export default {
    data: () => ({
        section: "",
    }),
    methods: {
        goProduct: function () {
            this.section = "product";
        },
        goStock: function () {
            this.section = "stock";
        },
        goSetting: function () {
            this.section = "setting";
        },
    },
    computed: {
    },
    components: {
        Header,
    },
}
</script>