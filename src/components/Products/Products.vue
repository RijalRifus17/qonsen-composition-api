<template>
    <the-navbar :addInChart="productToChart" />

    <div class="mt-20 mx-10">
        
        <div class="flex">
            <ListProduct @addChart="addChart(index)" :product="product" v-for="(product, index) in products" :key="index"/>       
        </div>

    </div>

</template>

<script>

import TheNavbar from '../TheNavbar.vue'
import ListProduct from './ListProduct.vue'

export default {
    components: {
        TheNavbar,
        ListProduct
    },
    props: [
        'products'
    ],

    data() {
        return {
            productToChart: {}
        }
    },

    methods: {
        addChart(index) {
            let data = {
                key: Math.random(),
                data: this.products[index]
            }
            this.productToChart = data
        }
    }
}
</script>