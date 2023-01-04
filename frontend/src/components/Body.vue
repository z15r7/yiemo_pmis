<template>
    <div class="bg-white p-4 rounded-md">
        <div class="grid grid-cols-1 sm:grid-cols-3 gap-4">
            <BodyItem v-for="item in products" :item="item" @add="add"/>
        </div>
    </div>
</template>

<script>
import BodyItem from './BodyItem.vue';

export default {
    data: () => ({
    }),
    props: ['products'],
    methods: {
        add: function (item) {
            this.$emit('add', item);
        }
    },
    computed: {
    },
    components: {
        BodyItem
    }
}
</script>