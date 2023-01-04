<template>
    <div class="w-full max-w-4xl place-item-center p-8 flex-row flex-grow-0 bg-slate-200 h-screen space-y-4">
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
            @add="add"
        />
        <Cart
            v-if="cart.length > 0"
            :cart="cart"
            @handleSubmit="handleSubmit"
            @handleCancel="handleCancel"
        />
    </div>
</template>

<script>
import Header from '/src/components/Header.vue';
import Body from '/src/components/Body.vue';
import Cart from '/src/components/Cart.vue';

export default {
    data: () => ({
        title: "yi.emo_nccu",
        section: "",
        selected: 0,
        showCart: false,
        menuItem: [
            {name: "銷貨", link: "product"},
            {name: "進貨", link: "stock"},
            {name: "設定", link: "setting"}
        ],
        products: [
            {name: "商品1", price: 100, stock: 10},
            {name: "商品2", price: 200, stock: 20},
            {name: "商品3", price: 300, stock: 30},
            {name: "商品1", price: 100, stock: 10},
            {name: "商品2", price: 200, stock: 20},
            {name: "商品3", price: 300, stock: 30},
            {name: "商品3", price: 300, stock: 30},
            {name: "商品3", price: 300, stock: 30},
            {name: "商品1", price: 100, stock: 10},
            {name: "商品2", price: 200, stock: 20},
            {name: "商品3", price: 300, stock: 30},
            {name: "商品3", price: 300, stock: 30},
            {name: "商品1", price: 100, stock: 10},
            {name: "商品2", price: 200, stock: 20},
            {name: "商品3", price: 300, stock: 30},
            {name: "商品1", price: 100, stock: 10},
            {name: "商品2", price: 200, stock: 20},
            {name: "商品3", price: 300, stock: 30},
            {name: "商品3", price: 300, stock: 30},
            {name: "商品3", price: 300, stock: 30},
            {name: "商品1", price: 100, stock: 10},
            {name: "商品2", price: 200, stock: 20},
            {name: "商品3", price: 300, stock: 30},
            {name: "商品3", price: 300, stock: 30},
        ],
        cart: []
    }),
    methods: {
        handleSelected: function (idx) {
            this.selected = idx;
        },
        add: function (item) {
            this.cart.push(item);
        },
        handleSubmit: function () {
            console.log("submit");
            this.cart = [];
        }
        ,handleCancel: function () {
            console.log("cancel");
            this.cart = [];
        }
    },
    computed: {
    },
    components: {
        Header,
        Body,
        Cart
    },
}
</script>