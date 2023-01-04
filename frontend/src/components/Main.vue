<template>
    <div class="w-full max-w-4xl place-item-center p-8 flex-row flex-grow-0 bg-slate-200 h-screen space-y-4">
        <Header
            :title="title"
            :selected="selected"
            :menuItem="menuItem"
            @handleSelected="handleSelected"
        />
        <div class="border border-slate-50 shadow bg-white p-2 rounded-md h-48">
            {{ selected }}
            {{ menuItem[selected].name }}
        </div>
    </div>
</template>

<script>
import Header from '/src/components/Header.vue';

export default {
    data: () => ({
        title: "yi.emo_nccu",
        section: "",
        selected: 0,
        menuItem: [
            {name: "商品", link: "product"},
            {name: "存貨", link: "stock"},
            {name: "設定", link: "setting"}
        ],
        products: [
            {name: "商品1", price: 100, stock: 10},
            {name: "商品2", price: 200, stock: 20},
            {name: "商品3", price: 300, stock: 30},
        ],
    }),
    methods: {
        handleSelected: function (idx) {
            this.selected = idx;
        }
    },
    computed: {
    },
    components: {
        Header,
    },
}
</script>