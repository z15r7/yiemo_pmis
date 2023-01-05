<template>
    <div class="grid grid-cols-1 sm:grid-cols-3 gap-4">
        <BodyItem v-for="item in materials" :item="item" @add="addStock"/>
    </div>
    <Stock
        v-if="stock.length > 0"
        :stock="stock"
        @addStock="addStock"
        @submitStock="submitStock"
        @clearStock="clearStock"
    />
</template>

<script>
import BodyItem from '/src/components/BodyItem.vue';
import Stock from '/src/components/Stock.vue';

export default {
    data: () => ({
    }),
    props: ['materials', 'stock'],
    methods: {
        addStock: function (item) {
            this.$emit('addStock', item);
        },
        clearStock: function () {
            this.$emit('clearStock');
        },
        submitStock: function () {
            this.$emit('submitStock');
        }
    },
    computed: {
    },
    components: {
        BodyItem,
        Stock
    }
}
</script>