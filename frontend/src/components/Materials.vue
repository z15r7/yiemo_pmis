<template>
    <div class="grid grid-cols-1 sm:grid-cols-3 gap-4">
        <BodyItem2 v-for="item in materials" :item="item" :id="item.id" @click="handleUpdateModal"/>
        <div
            class="border border-slate-50 shadow shadow-slate-300 bg-white p-4 rounded-md cursor-pointer"
            @click="showModal"
        >
            <p>新增原料</p>
        </div>
    </div>
    <div class="fixed w-screen min-h-screen top-0 left-0 backdrop-blur" v-if="showAddMaterialModal">
        <!-- <div class="fixed backdrop-blur w-full h-full" v-if="showAddMaterialModal" @click="hideModal">
        </div> -->
        <div class="flex justify-center place-items-center min-h-screen">
            <div class="flex flex-col gap-4 border border-slate-50 shadow shadow-slate-300 bg-white p-4 rounded-md">
                <div class="flex flex-col gap-4">
                    <div class="flex flex-col">
                        <label for="name">品項名稱</label>
                        <input type="text" name="name" id="name" v-model="modalForm.name" class="border rounded">
                    </div>
                    <div class="flex flex-col">
                        <label for="type">類別</label>
                        <select name="type" id="type" v-model="modalForm.type">
                            <option value="fixed">固定用量</option>
                            <option value="flexible">不定用量</option>
                        </select>
                    </div>  
                </div>
                <div class="flex justify-end gap-4">
                    <button class="border rounded" @click="handleCancel">取消</button>
                    <button class="border rounded" @click="handleSubmit">確認</button>
                </div>
            </div>
        </div>
    </div>
    <div class="fixed w-screen min-h-screen top-0 left-0 backdrop-blur" v-if="isShowUpdateModal">
        <!-- <div class="fixed backdrop-blur w-full h-full" v-if="showAddMaterialModal" @click="hideModal">
        </div> -->
        <div class="flex justify-center place-items-center min-h-screen">
            <div class="flex flex-col gap-4 border border-slate-50 shadow shadow-slate-300 bg-white p-4 rounded-md">
                <div class="flex flex-col gap-4">
                    <div>{{anchorUpdate}}</div>
                    <button>耗盡</button>
                    <button>盤點</button>
                    <button @click="hideUpdateModal">關閉</button>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import BodyItem2 from '/src/components/BodyItem2.vue';

const defaultForm = {
    name: '新原料',
    type: 'fixed',
    stock: 0,
    estStock: 0,
}

export default {
    data: () => ({
        showAddMaterialModal: false,
        isShowUpdateModal: false,
        anchorUpdate: null,
        modalForm: JSON.parse(JSON.stringify(defaultForm))
    }),
    props: ['materials'],
    methods: {
        handleSubmit: function () {
            this.modalForm.id = new Date().getTime();
            this.$emit('addMaterial', this.modalForm);
            this.hideModal();
        },
        handleCancel: function () {
            this.hideModal();
        },
        showModal: function () {
            this.modalForm = JSON.parse(JSON.stringify(defaultForm));
            this.showAddMaterialModal = true;
        },
        hideModal: function () {
            this.showAddMaterialModal = false;
        },
        showUpdateModal: function () {
            this.isShowUpdateModal = true;
        },
        hideUpdateModal: function () {
            this.anchorUpdate = null;
            this.isShowUpdateModal = false;
        },
        handleUpdateModal: function (item) {
            this.anchorUpdate = item.target.id;
            this.showUpdateModal();
        }
    },
    computed: {
    },
    components: {
        BodyItem2
    }
}
</script>