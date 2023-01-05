<template>
    <div class="grid grid-cols-1 sm:grid-cols-3 gap-4">
        <BodyItem v-for="item in products" :item="item"/>
        <div
            class="border border-slate-50 shadow shadow-slate-300 bg-white p-4 rounded-md cursor-pointer"
            @click="showModal"
        >
            <p>新增品項</p>
        </div>
    </div>
    <div class="fixed backdrop-blur w-screen min-h-screen top-0 left-0" v-if="showAddProductModal">
        <div class="flex justify-center place-items-center min-h-screen">
            <div class="flex flex-col gap-4 border border-slate-50 shadow shadow-slate-300 bg-white p-4 rounded-md">
                <div class="flex flex-col gap-4">
                    <div class="flex flex-col">
                        <label for="name">品項名稱</label>
                        <input type="text" name="name" id="name" v-model="modalForm.name" class="border rounded">
                    </div>
                    <div class="flex flex-col">
                        <label for="price">價格</label>
                        <input type="number" name="price" id="price" v-model="modalForm.price" class="border rounded">
                    </div>
                    <div>
                        <div v-for="i in modalForm.materials">{{i}}</div>
                    </div>
                    <div>
                        <select name="materials" id="materials">
                            <option value="">選擇原料</option>
                            <option :value="i.id" v-for="i in materials">{{`${i.id}-${i.name}`}}</option>
                        </select>
                        <button @click="putMaterial">Add</button>
                    </div>
                </div>
                <div class="flex justify-end gap-4">
                    <button class="border rounded" @click="handleCancel">取消</button>
                    <button class="border rounded" @click="handleSubmit">確認</button>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import BodyItem from '/src/components/BodyItem.vue';

const defaultForm = {
    name: '新產品',
    price: 0,
    materials: []
}

export default {
    data: () => ({
        showAddProductModal: false,
        modalForm: JSON.parse(JSON.stringify(defaultForm))
    }),
    props: ['add', 'products', 'materials'],
    methods: {
        handleSubmit: function () {
            this.modalForm.id = new Date().getTime();
            this.$emit('addProduct', this.modalForm);
            this.hideModal();
        },
        handleCancel: function () {
            this.hideModal();
        },
        showModal: function () {
            this.modalForm = JSON.parse(JSON.stringify(defaultForm));
            this.showAddProductModal = true;
        },
        hideModal: function () {
            this.showAddProductModal = false;
        },
        putMaterial: function () {
            document.getElementById('materials').value && this.modalForm.materials.push(document.getElementById('materials').value);
        }
    },
    computed: {
    },
    components: {
        BodyItem
    }
}
</script>