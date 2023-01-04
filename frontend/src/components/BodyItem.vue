<template>
    <div
        class="border border-slate-50 shadow shadow-slate-300 bg-white p-4 rounded-md"
        @click="add"
    >
        <p>{{ item.name }}</p>
        <p>{{ handlePrice(item.price) }}</p>
    </div>
</template>

<script>
    export default {
        data: () => ({
        }),
        props: ['item'],
        methods: {
            handleSelected: function (idx) {
                this.$emit('handleSelected', idx);
            },
            handlePrice: function (value) {
                return `$${JSON.stringify(value)}`;
            },
            add: function () {
                this.$emit('add', this.item);
            }
        },
        computed: {
        },
    }
</script>