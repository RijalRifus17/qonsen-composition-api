<template>
    <div 
        class="fixed top-0 bg-white border-b-4 
            border-solid border-green-500 w-full left-0 
            right-0 h-16 flex items-center justify-between px-10"
        >

        <div class="text-2xl font-bold">
            RIFUS SHOP
        </div>

        <div>
            <button @click="openTheChart()" class="border-2 relative outline-white border-solid border-green-500 p-2 rounded-lg">
                {{ charts.length }} | {{ priceTotal }}

                <div 
                    class="absolute bg-white border-2 border-solid" 
                    :class="{ hidden: !openChart, block: openChart  }"
                    style="width:300px;right:50%;top:100%;">
                    
                    <div v-if="charts.length">
                        <ProductInChart @removeProduct="removeProduct(index)" :product="product" v-for="(product, index) in charts" :key="index"/>
                    </div>
                    <div v-else class="p-2">
                        Tidak ada barang
                    </div>
                    
                </div>
            </button>
        </div>
    </div>
</template>



<script>

import ProductInChart from './ProductInChart.vue'

export default {
    components: {
        ProductInChart
    },
    props: [
        'addInChart'
    ],

    data() {
        return {
            charts: [],
            openChart: false,
            newProduct: {}
        }
    },

    computed: {
        priceTotal() {
            let price = 0;
            this.charts.forEach(product => {
                
                price += product.price
                if(product.count > 1) {
                    price *= product.count
                }
            });

            return this.toIdr(price)
        }
    },

    methods: {
        removeProduct(index) {
            const product = this.charts[index]

            if(product.count > 1) {
                product.count--
            } else {
                this.charts.splice(index, 1)
            }
        },

        toIdr(angka) {
            let rupiah = '';		
            let angkarev = angka.toString().split('').reverse().join('');
            for(let i = 0; i < angkarev.length; i++) if(i%3 == 0) rupiah += angkarev.substr(i,3)+'.';

            return 'Rp. '+rupiah.split('',rupiah.length-1).reverse().join('');
        },

        openTheChart() {
            this.openChart = !this.openChart
        },

        addToChart() {
            let index = this.charts.map(function(x) {return x.id; }).indexOf(this.addInChart.data.id);
            // var objectFound = array[elementPos];
            console.log(index);
            if(index == -1) {
                this.addInChart.data.count = 1
                this.charts.push(this.addInChart.data)  
            } else {
                this.charts[index].count++ 
            }
            // this.charts.push(this.addInChart.data)        
        }
    },

    watch: {
        addInChart() {
            console.log('a');
            this.addToChart()
        },
    }
}
</script>