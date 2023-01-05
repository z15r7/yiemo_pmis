<template>
    <div class="bg-white p-4 rounded-md">
        <Sales
            v-if="selected === 0"
            :products="products"
            :cart="cart"
            @addCart="addCart"
            @clearCart="clearCart"
        />
        <Purchases
            v-if="selected === 1"
            :materials="materials"
            :stock="stock"
            @addStock="addStock"
            @submitStock="submitStock"
            @clearStock="clearStock"
        />
        <Products
            v-if="selected === 2"
            :products="products"
            :materials="materials"
            @addProduct="addProduct"
        />
        <Discounts
            v-if="selected === 3"
        />
        <Materials
            v-if="selected === 4"
            :materials="materials"
            @addMaterial="addMaterial"
        />
        <Statistics
            v-if="selected === 5"
        />
        <Settings
            v-if="selected === 6"
        />
    </div>
</template>

<script>
import Discounts from '/src/components/Discounts.vue';
import Materials from '/src/components/Materials.vue';
import Products from '/src/components/Products.vue';
import Purchases from '/src/components/Purchases.vue';
import Sales from '/src/components/Sales.vue';
import Settings from '/src/components/Settings.vue';
import Statistics from '/src/components/Statistics.vue';

export default {
    data: () => ({
    }),
    props: ['selected', 'products', 'materials', 'cart', 'stock'],
    methods: {
        addProduct: function (item) {
            this.$emit('addProduct', item);
        },
        addMaterial: function (item) {
            this.$emit('addMaterial', item);
        },
        addCart: function (item) {
            this.$emit('addCart', item);
        },
        addStock: function (item) {
            this.$emit('addStock', item);
        },
        clearCart: function () {
            this.$emit('clearCart');
        },
        submitStock: function () {
            this.$emit('submitStock');
        },
        clearStock: function () {
            this.$emit('clearStock');
        },
    },
    computed: {
    },
    components: {
        Discounts,
        Materials,
        Products,
        Purchases,
        Sales,
        Settings,
        Statistics
    },
}
</script>