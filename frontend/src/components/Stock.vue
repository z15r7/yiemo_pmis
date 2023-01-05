<template>
    <div class="fixed h-1/2 w-full bottom-0 left-0 shadow-xl bg-slate-200 p-4">
        <div class="grid grid-cols-1 gap-4 p-4">
            <div
                class="border border-slate-50 shadow shadow-slate-300 bg-white py-2 px-4 rounded-md"
                v-for="i in stock"
            >
                {{`${i.id}-${i.name}`}}
                {{`${i.type}`}}
            </div>
        </div>
        <div class="fixed w-full bottom-0 left-0">
            <div class="grid grid-cols-1 sm:grid-cols-2 gap-4 p-4">
                <button
                    class="bg-red-500 shadow rounded-md py-2 text-white"
                    @click="handleCancel"
                >
                    Cancel
                </button>
                <button
                    class="bg-blue-500 shadow rounded-md py-2 text-white"
                    @click="handleSubmit"
                >
                    Submit
                </button>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data: () => ({
    }),
    props: ['stock'],
    emits: ['submitStock', 'clearStock'],
    methods: {
        handleSubmit: function () {
            this.$emit('submitStock');
        },
        handleCancel: function () {
            this.$emit('clearStock');
        }
    },
    computed: {
    },
}
</script>