<template>
  <div class="flex justify-between ml-6 mr-6 mt-4">
    <nuxt-link to="/">
      <span>
        <img src="~/assets/logo.png" class="logo" height="150" width="150" />
      </span>
    </nuxt-link>

    <div class="flex items-center space-x-4">
      <div v-if="$strapi.user" class="space-x-4">
        <nuxt-link to="/mycourses">My Courses</nuxt-link>
        <button @click="logout">Logout</button>
      </div>
      <nuxt-link v-else to="/login">
        Login
      </nuxt-link>
      <button class="snipcart-checkout flex items-center">
        <Cart />
        <span
          class="snipcart-total-price ml-3 font-semibold text-sm text-indigo-500"
        ></span>
      </button>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    async logout() {
      let res = await this.$strapi.logout();
      this.$router.push("/");
    },
  },
};
</script>

<style></style>
