<template>
    <div
        class="border border-slate-50 shadow shadow-slate-300 bg-white p-4 rounded-md cursor-pointer"
        @click="handleAdd"
    >
        <p>{{ item.id }}</p>
        <p>{{ item.name }}</p>
        <p v-if="typeof item.price === 'number' && item.price !== NaN">{{ handlePrice(item.price) }}</p>
        <p v-if="typeof item.cost === 'number' && item.cost !== NaN">{{ handlePrice(item.cost) }}</p>
        <p v-if="typeof item.type === 'string' ">{{ item.type }}</p>
        <p v-if="typeof item.stock === 'number' && item.stock !== NaN">庫存：{{ item.stock }}</p>
        <p v-if="typeof item.sales === 'number' && item.sales !== NaN">銷量：{{ item.sales }}</p>
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
            handleAdd: function () {
                this.$emit('add', this.item);
            }
        },
        computed: {
        },
    }
</script>