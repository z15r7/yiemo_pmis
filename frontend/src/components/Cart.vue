<template>
    <div class="fixed h-1/2 w-full bottom-0 left-0 shadow-xl bg-slate-200 p-4">
        <div class="grid grid-cols-1 gap-4 p-4">
            <div
                class="border border-slate-50 shadow shadow-slate-300 bg-white py-2 px-4 rounded-md"
                v-for="i in cart"
            >
                {{`${i.name}-${i.price}`}}
            </div>
        </div>
        <div class="fixed w-full bottom-0 left-0">
            <div class="grid grid-cols-1 sm:grid-cols-2 gap-4 p-4">
                <button
                    class="bg-blue-500 shadow rounded-md py-2 text-white"
                    @click="handleSubmit"
                >Submit</button>
                <button
                    class="bg-red-500 shadow rounded-md py-2 text-white"
                    @click="handleCancel"
                >Cancel</button>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data: () => ({
    }),
    props: ['cart'],
    methods: {
        handleSubmit: function () {
            this.$emit('handleSubmit');
        },
        handleCancel: function () {
            this.$emit('handleCancel');
        }
    },
    computed: {
    },
}
</script>