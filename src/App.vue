<template>
  <products :products="products" />
</template>

<script>

import Products from "./components/Products/Products.vue"

export default {
  components: {
    Products
  },
  data() {
    return {
      products: [
                {
                    id: 1,
                    name: "Samsung Galaxy M31",
                    thumbnail: "https://ecs7.tokopedia.net/img/cache/900/product-1/2020/4/8/765813775/765813775_3d0fc42e-f351-47ed-b559-b87066eb1c7c_954_954.jpg",
                    price: 3850000
                },
                {
                    id: 2,
                    name: "Samsung Galaxy A51 128GB A515F Blue",
                    thumbnail: "https://ecs7.tokopedia.net/img/cache/900/attachment/2020/11/23/29652022/29652022_cd38b8fd-b87c-450d-8ec6-b32bd6357b2e.jpg",
                    price: 4199000
                },
                {
                    id: 3,
                    name: "Samsung Galaxy S10e",
                    thumbnail: "https://ecs7.tokopedia.net/img/cache/900/VqbcmM/2020/11/2/71aac36f-8c2e-4b27-b098-9647d4c15a7d.jpg",
                    price: 3350000
                },
                {
                    id: 4,
                    name: "Samsung Note 20 Ultra|",
                    thumbnail: "https://ecs7.tokopedia.net/img/cache/900/VqbcmM/2020/11/9/ff992ef1-798f-442b-b791-c73f8b5560d1.jpg",
                    price: 10770000
                },
                {
                    id: 5,
                    name: "Samsung Galaxy A01",
                    thumbnail: "https://ecs7.tokopedia.net/img/cache/900/product-1/2020/3/11/856804/856804_a7c83c4e-ba24-49ae-bd4c-ed84fa1c0567_2048_2048.jpg",
                    price: 1165000
                }
      ]
    }
  }
}
</script>