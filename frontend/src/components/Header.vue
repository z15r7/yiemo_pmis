<template>
    <div class="flex justify-center place-items-center shadow border border-slate-50 bg-white p-2 rounded-md">
        <div></div>
        <div class="w-full">
            <p class="text-xl font-bold text-center">{{ title }}</p>
        </div>
        <div></div>
    </div>
    <div class="flex flex-grow-0">
        <div class="flex justify-center flex-grow-0 w-full border border-slate-300 bg-white p-2 rounded-l-xl">
            <button class="`w-full -m-2 p-2">商品</button>
        </div>
        <div class="flex justify-center flex-grow-0 w-full border border-slate-300 bg-white p-2">
            <button class="w-full -m-2 p-2">存貨</button>
        </div>
        <div class="flex justify-center flex-grow-0 w-full border border-slate-300 bg-white p-2 rounded-r-xl">
            <button class="w-full -m-2 p-2">設定</button>
        </div>
    </div>
</template>

<script>
export default {
    data: () => ({
        title: "yi.emo_nccu",
        item: [
            {name: "商品", link: "product", selected: false},
            {name: "存貨", link: "stock", selected: false},
            {name: "設定", link: "setting", selected: false}
            // {name: "商品", link: "product", func: goProduct()},
            // {name: "存貨", link: "stock", func: goStock()},
            // {name: "設定", link: "setting", func: goSetting()}
        ]
    }),
    methods: {
    },
    computed: {
    },
}
</script>