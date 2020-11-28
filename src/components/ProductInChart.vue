<template>

    <div class="flex w-full cursor-default justify-start border-b border-solid p-2">
        <div class="mr-2">
            <img :src="product.thumbnail" class="w-10 h-10" alt="">
        </div>
        <div class="text-left w-full">
            {{ product.name }}
            <div class="flex justify-between">
                <div class="text-xs">
                    {{ product.count }} Barang
                </div>
                <div class="text-green-500 text-sm font-bold">
                    {{ toIdr }}
                </div>
            </div>
        </div>
        <div>
            <button @click.stop="removeProduct" class="bg-red-500 text-white p-1 rounded-md text-xs">
                Hapus
            </button>
        </div>
    </div>

</template>

<script>
export default {
    props: [
        'product'
    ],
    emits: ['removeProduct'],

    computed: {
        toIdr() {
            let rupiah = '';		
            let angkarev = this.priceTotal.toString().split('').reverse().join('');
            for(let i = 0; i < angkarev.length; i++) if(i%3 == 0) rupiah += angkarev.substr(i,3)+'.';

            return 'Rp. '+rupiah.split('',rupiah.length-1).reverse().join('');
        },
        priceTotal() {
            return this.product.price * this.product.count
        }
    },

    methods: {
        removeProduct() {
            this.$emit('removeProduct')
        }
    }
}
</script>