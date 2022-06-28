<template>
  <div class="md:mx-64 mx-4 px-4 my-24 py-4 border border-gray-400">
    <div class="flex justify-between">
      <h1 class="md:text-3xl text-xl font-bold">Detail Products</h1>
      <router-link
        to="/list-product"
        class="px-10 text-white bg-red-500 py-2 hover:opacity-70 transition"
        >Back</router-link
      >
    </div>
    <div class="mt-10">
      <div class="card">
        <img :src="this.prd.thumbnail" class="w-full" />
        <h1 class="mt-3 text-3xl mb-2">{{ this.prd.title }}</h1>
        <h3>Price : ${{ this.prd.price }}</h3>
        <h3>Rating : {{ this.prd.rating }}</h3>
        <h3>Stock : {{ this.prd.stock }}</h3>
        <h3>Brand : {{ this.prd.brand }}</h3>
        <h3>Category : {{ this.prd.brand }}</h3>

        <h2 class="mt-3 font-semibold text-lg">Images of Products</h2>
        <div class="grid grid-cols-3 gap-2">
          <div class="card" v-for="(image, key) in this.prd.images" :key="key">
            <img :src="image" class="mt-2" />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      products: [],
      prd: [],
      productTitle: "",
      productPrice: "",
    };
  },
  methods: {
    async fetchProduct(index) {
      const res = await axios.get("https://dummyjson.com/products/" + index);
      console.log(res.data);
      this.prd = res.data;
    },
  },

  mounted() {
    this.fetchProduct(this.$route.params.id);
  },
};
</script>