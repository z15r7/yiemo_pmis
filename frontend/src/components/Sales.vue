<template>
    <div class="grid grid-cols-1 sm:grid-cols-3 gap-4">
        <BodyItem v-for="item in products" :item="item" @add="addCart"/>
    </div>
    <Cart
        v-if="cart.length > 0"
        :cart="cart"
        @addCart="addCart"
        @clearCart="clearCart"
    />
</template>

<script>
import BodyItem from '/src/components/BodyItem.vue';
import Cart from '/src/components/Cart.vue';

export default {
    data: () => ({
    }),
    props: ['products', 'cart'],
    methods: {
        addCart: function (item) {
            this.$emit('addCart', item);
        },
        clearCart: function () {
            this.$emit('clearCart');
        },
    },
    computed: {
    },
    components: {
        BodyItem,
        Cart
    }
}
</script>