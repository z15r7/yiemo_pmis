<template>
    <div class="place-item-center w-4/6 p-8 flex-row flex-grow-0 bg-slate-200 h-screen">
        <Header />
        <div class="my-4 border border-slate-50 shadow bg-white p-2 rounded-md">{{ x }}</div>
        <div class="my-4 border border-slate-50 shadow bg-white p-2 rounded-md" v-if="x===1111">{{ "x===1111" }}</div>
        <div class="my-4 border border-slate-50 shadow bg-white p-2 rounded-md" v-if="x>1111">{{ showAbc }}</div>
        <div class="flex justify-center my-4 shadow bg-blue-500 rounded-md p-2 text-white">
            <button class="w-full -m-2 p-2" @click="add">add</button>
        </div>
        <div class="flex flex-grow-0 space-x-4">
            <div class="flex justify-center flex-grow-0 w-full border border-slate-50 shadow bg-white p-2 rounded-md">
                <button class="`w-full -m-2 p-2" @click="goProduct">商品</button>
            </div>
            <div class="flex justify-center flex-grow-0 w-full border border-slate-50 shadow bg-white p-2 rounded-md">
                <button class="w-full -m-2 p-2" @click="goStock">存貨</button>
            </div>
            <div class="flex justify-center flex-grow-0 w-full border border-slate-50 shadow bg-white p-2 rounded-md">
                <button class="w-full -m-2 p-2" @click="goSetting">設定</button>
            </div>
        </div>
        <div class="my-4 border border-slate-50 shadow bg-white p-2 rounded-md h-48">{{ section }}</div>
    </div>
</template>

<script>
import Header from '/src/components/Header.vue';

export default {
    data: () => ({
        x: 1111,
        test: "testaaa",
        section: "",
    }),
    methods: {
        add: function () {
            this.x += 100;
        },
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
        showAbc: function () {
            return `x>1111, ${this.test}`;
        },
    },
    components: {
        Header,
    },
}
</script>