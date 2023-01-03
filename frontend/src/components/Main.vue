<template>
    <div class="">
        <p>{{ x }}</p>
        <p v-if="x===1111">{{ "x===1111" }}</p>
        <p v-if="x>1111">{{ showAbc }}</p>
    </div>
    <button @click="add">Add</button>
</template>

<script>
export default {
    data: () => ({
        x: 1111,
        test: "testaaa",
    }),
    methods: {
        add: function () {
            this.x += 100;
        },
    },
    computed: {
        showAbc: function () {
            return `x>1111, ${this.test}`;
        },
    },
}
</script>