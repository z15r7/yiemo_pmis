<template>
    <div class="border border-slate-50 shadow bg-white p-2 rounded-md">
        <div class="grid grid-cols-1 sm:grid-cols-3 gap-2">
            <div class="border border-slate-50 shadow bg-blue-500 p-2 rounded-md" v-for="item in products">
                <p>{{ item.name }}</p>
                <p>{{ handlePrice(item.price) }}</p>
            </div>
        </div>
        
    </div>
</template>

<script>
    export default {
        data: () => ({
        }),
        props: ['selected', 'menuItem', 'products'],
        methods: {
            handleSelected: function (idx) {
                this.$emit('handleSelected', idx);
            },
            handlePrice: function (value) {
                return `$${JSON.stringify(value)}`;
            }
        },
        computed: {
        },
    }
</script>