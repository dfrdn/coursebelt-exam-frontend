<template>
  <div class="flex justify-between ml-6 mr-6 mt-4">
    <nuxt-link to="/">
      <span class="emoji">
        <img src="~/assets/logo.png" class="logo" height="150" width="150" />
      </span>
    </nuxt-link>

    <div class="flex items-center space-x-4">
      <button class="snipcart-customer-signin">
        login
      </button>
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
export default {};
</script>

<style>
.emoji {
  font-size: 30px;
}
</style>
