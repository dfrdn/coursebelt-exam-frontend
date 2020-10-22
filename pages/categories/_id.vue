<template>
  <courses :courses="this.category.courses" :error="error" />
</template>

<script>
export default {
  data() {
    return {
      category: {},
      error: null,
    };
  },
  async mounted() {
    try {
      this.category = await this.$strapi.$categories.findOne(
        this.$route.params.id
      );
    } catch (error) {
      this.error = error;
    }
  },
};
</script>
