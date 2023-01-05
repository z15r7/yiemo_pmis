<template>
    <div class="w-full max-w-4xl place-item-center p-8 flex-row flex-grow-0 bg-slate-200 space-y-4 min-h-screen">
        <Header
            :title="title"
            :selected="selected"
            :menuItem="menuItem"
            @handleSelected="handleSelected"
        />
        <Body
            :selected="selected"
            :menuItem="menuItem"
            :products="products"
            @addProduct="addProduct"
            :materials="materials"
            @addMaterial="addMaterial"
            :cart="cart"
            @addCart="addCart"
            @clearCart="clearCart"
            :stock="stock"
            @addStock="addStock"
            @submitStock="submitStock"
            @clearStock="clearStock"
        />
    </div>
</template>

<script>
import Header from '/src/components/Header.vue';
import Body from '/src/components/Body.vue';

export default {
    data: () => ({
        title: "yi.emo_nccu",
        section: "",
        selected: 0,
        showCart: false,
        showStock: false,
        menuItem: [
            {name: "銷貨", link: "sale"},
            {name: "進貨", link: "purchase"},
            {name: "商品", link: "product"},
            {name: "折扣", link: "discount"},
            {name: "原料", link: "material"},
            {name: "統計", link: "statistic"},
            {name: "設定", link: "setting"}
        ],
        products: [],
        materials: [],
        cart: [],
        stock: [],
    }),
    methods: {
        handleSelected: function (idx) {
            this.selected = idx;
        },
        addProduct: function (item) {
            this.products.push(item);
        },
        addMaterial: function (item) {
            this.materials.push(item);
        },
        addCart: function (item) {
            this.cart.push(item);
        },
        addStock: function (item) {
            this.stock.push(item);
        },
        clearCart: function () {
            this.cart = [];
        },
        clearStock: function () {
            this.stock = [];
        },
        submitStock: function () {
            this.stock.forEach((material) => {
                this.materials.find((item) => {
                    if (item.id === material.id)
                        item.stock += 1;
                });
            });
            this.clearStock();
        },
    },
    computed: {
    },
    components: {
        Header,
        Body,
    },
}
</script>