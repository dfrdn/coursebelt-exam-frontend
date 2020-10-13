<template>
  <div>
    <courses :courses="$strapi.user.courses" :error="error" />
  </div>
</template>

<script>
import Vue from "vue";

export default Vue.extend({
  middleware: "auth",
});
</script>

<style scoped></style>
