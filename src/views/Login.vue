<template>
  <div class="md:px-80 md:py-32 px-4 py-12">
    <div class="container border md:px-6 px-4 py-12 border-gray-200">
      <h1 class="text-3xl font-semibold">Login</h1>
      <form class="rounded-3xl py-6" @submit.prevent="login()">
        <div class="mb-6">
          <label
            for="username"
            class="
              block
              mb-2
              text-sm
              font-medium
              text-gray-900
              dark:text-gray-300
            "
            >Masukan Username</label
          >
          <input
            v-model="username"
            type="text"
            id="username"
            name="username"
            class="
              bg-gray-50
              border border-gray-300
              text-gray-900 text-sm
              rounded-lg
              focus:ring-blue-500 focus:border-blue-500
              block
              w-full
              p-2.5
              dark:bg-gray-700
              dark:border-gray-600
              dark:placeholder-gray-400
              dark:text-white
              dark:focus:ring-blue-500
              dark:focus:border-blue-500
            "
            placeholder="Username"
            required
          />
        </div>
        <div class="mb-6">
          <label
            for="password"
            class="
              block
              mb-2
              text-sm
              font-medium
              text-gray-900
              dark:text-gray-300
            "
            >Masukan password</label
          >
          <input
            type="password"
            name="password"
            v-model="password"
            id="password"
            placeholder="Password"
            class="
              bg-gray-50
              border border-gray-300
              text-gray-900 text-sm
              rounded-lg
              focus:ring-indigo-500 focus:border-indigo-500
              block
              w-full
              p-2.5
              dark:bg-gray-700
              dark:border-gray-600
              dark:placeholder-gray-400
              dark:text-white
              dark:focus:ring-blue-500
              dark:focus:border-blue-500
            "
            required
          />
        </div>

        <button
          type="submit"
          class="
            text-white
            bg-indigo-700
            hover:bg-indigo-800
            focus:ring-4 focus:outline-none focus:ring-indigo-300
            font-medium
            rounded-lg
            text-sm
            w-full
            sm:w-auto
            px-5
            py-2.5
            text-center
            dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800
          "
        >
          Submit
        </button>
      </form>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data: () => ({
    username: "",
    password: "",
  }),
  methods: {
    async login() {
      const auth = { username: this.username, password: this.password };
      try {
        await axios
          .post("https://dummyjson.com/auth/login", auth)
          .then((res) => res.data, this.$router.push("/list-product"));
        alert("sukses login");
      } catch (err) {
        this.$router.push("/");
        this.error = err.message;
      }
    },
  },
};
</script>