<template>
    <div class="flex justify-center place-items-center shadow border border-slate-50 bg-white p-2 rounded-md">
        <div></div>
        <div class="w-full">
            <p class="text-xl font-bold text-center">{{ title }}</p>
        </div>
        <div></div>
    </div>
    <div class="flex flex-grow-0">
        <button
            class="flex justify-center flex-grow-0 w-full border border-slate-300 p-2"
            :class="[
                {'bg-blue-500 text-white': idx === selected},
                {'bg-white': idx !== selected},
                {'rounded-l-xl': idx === 0},
                {'rounded-r-xl': idx === menuItem.length - 1}
            ]"
            @click="handleSelected(idx)"
            v-for="i, idx in menuItem"
        >
            <p>{{ i.name }}</p>
        </button>
    </div>
</template>

<script>
export default {
    data: () => ({
    }),
    props: ['title', 'selected', 'menuItem'],
    emits: ['handleSelected'],
    methods: {
        handleSelected: function (idx) {
            this.$emit('handleSelected', idx);
        }
    },
    computed: {
    },
}
</script>