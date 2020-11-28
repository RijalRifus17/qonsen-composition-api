<template>
    <div class="bg-white shadow-lg rounded-lg w-2/12 mx-2 overflow-hidden flex flex-col justify-between">
        <div>
            <img :src="product.thumbnail" class="w-full object-fit" alt="">
        </div>
        <div class="p-2">
            <div>
                {{ product.name }}
            </div>
            <div class="mt-2 text-green-500">
                {{ toIdr }}
            </div>
            <div class="mt-2" @click="addChart">
                <button class="w-full bg-white border border-2 border-green-500 p-2 rounded-lg">
                    Ambil
                </button>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: [
        'product'
    ],
    emits: ['addChart'],

    computed: {
        toIdr() {
            let rupiah = '';		
            let angkarev = this.product.price.toString().split('').reverse().join('');
            for(let i = 0; i < angkarev.length; i++) if(i%3 == 0) rupiah += angkarev.substr(i,3)+'.';

            return 'Rp. '+rupiah.split('',rupiah.length-1).reverse().join('');
        },
    },

    methods: {
        addChart() {
            this.$emit('addChart')
        }
    }
}
</script>