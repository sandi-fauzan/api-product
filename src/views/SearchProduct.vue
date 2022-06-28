<template>
  <div class="md:px-72 md:py-20 px-4 py-4">
    <div class="border border-gray-500 rounded-md px-4 py-4">
      <div class="flex justify-between">
        <h1 class="text-2xl font-semibold">Search Products</h1>
        <router-link
          to="/list-product"
          class="px-10 text-white bg-red-500 py-2 hover:opacity-70 transition"
          >Back</router-link
        >
      </div>
      <input
        type="text"
        class="mt-10 w-full"
        v-model="searchInput"
        @keyup.prevent="searchProduct"
      />
      <div class="search-card mt-6">
        <ul>
          <li
            class="flex my-2"
            v-for="(product, index) in products"
            :key="index"
          >
            <img :src="product.thumbnail" class="w-44" />
            <div class="block ml-4">
              <router-link
                :to="'/detail-product/' + product.id"
                class="hover:underline font-semibold text-lg"
                >{{ product.title }}</router-link
              >
              <h3>Price : ${{ product.price }}</h3>
              <h3>Rating : {{ product.rating }}</h3>
              <h3>Stock : {{ product.stock }}</h3>
            </div>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      //   searchResult: [],
      searchInput: "",
      searchResult: null,
      products: [],
    };
  },
  async mounted() {
    // await axios
    //   .get("https://dummyjson.com/products/search?q=")
    //   .then((response) => {
    //     this.products = response.data.products;
    //     console.log(this.data.products);
    //   })
    //   .catch((err) => {
    //     console.log(err);
    //   });
  },
  methods: {
    // debounceSearch(event) {
    //   clearTimeout(this.debounce);
    //   this.debounce = setTimeout(() => {
    //     this.fetchSearch(event.target.value);
    //   }, 500);
    // },
    // async fetchSearch(e) {
    //   try {
    //     const res = await axios.get(
    //       "https://dummyjson.com/products/search?q=" + e
    //     );
    //     this.searchResult = res.data;
    //   } catch (err) {
    //     console.log(err);
    //   }
    // },

    async searchProduct() {
      //   const searchResult = this.searchResult;
      //   const searchInput = this.searchInput;
      await axios
        .get("https://dummyjson.com/products/search?q=" + this.searchInput)
        .then((response) => {
          this.products = response.data.products;
          console.log(this.products);
        })
        .catch((err) => {
          console.log(err);
        });
    },
  },
};
</script>