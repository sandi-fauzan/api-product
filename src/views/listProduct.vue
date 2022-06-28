<template>
  <div class="block">
    <router-link
      to="/"
      class="
        px-10
        text-white
        bg-red-700
        py-2
        hover:opacity-70
        transition
        right-0
        text-right
        absolute
      "
      >Logout</router-link
    >
  </div>
  <div class="md:px-72 md:py-24">
    <div class="md:flex md:justify-between block">
      <h1 class="text-3xl font-bold m-4 md:m-0">List Products</h1>
      <router-link
        to="/search-product"
        class="
          px-10
          ml-4
          md:ml-0
          text-white
          bg-indigo-500
          py-2
          hover:opacity-70
          transition
        "
        >Search Product</router-link
      >
    </div>
    <div class="md:grid md:grid-cols-4 md:gap-4 block mt-12">
      <div
        class="card px-2 pb-2 border"
        v-for="(product, index) in products"
        :key="index"
      >
        <img
          :src="product.thumbnail"
          class="w-full bg-cover object-cover h-44 mt-2"
        />
        <router-link
          class="text-lg hover:underline"
          :to="'/detail-product/' + product.id"
          >{{ product.title }}</router-link
        >
        <h3 class="text-red-600">
          ${{ product.price }}
          <!-- <span class="text-xs text-gray-400"
            >discount {{ product.discountPercentage }}%</span
          > -->
        </h3>
        <h3>{{ product.rating }}</h3>
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
      productTitle: "",
      productPrice: "",
    };
  },
  methods: {
    // async tambahKomentar() {
    //   const res = await axios.post("http://localhost:3000/comments", {
    //     body: this.komentar,
    //   });
    //   this.items = [...this.items, res.data];
    //   this.komentar = "";
    //   this.$toast.success(`Komentar ditambahkan`);
    // },
    // async getId(index) {
    //   const res = await axios
    //     .get(`http://localhost:3000/comments/${index}`)
    //     .then();
    //   this.idData = res.data.id;
    //   this.komen = res.data.body;
    // },
  },
  async mounted() {
    await axios
      .get("https://dummyjson.com/products")
      .then((response) => {
        this.products = response.data.products;
        console.log(this.data.products);
      })
      .catch((err) => {
        console.log(err);
      });
  },
};
</script>