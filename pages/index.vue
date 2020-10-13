<template>
  <courses :courses="courses" :error="error" :storeUrl="storeUrl" />
</template>

<script>
export default {
  data() {
    return {
      courses: [],
      storeUrl: process.env.storeUrl,
      error: null,
    };
  },
  async mounted() {
    try {
      this.courses = await this.$strapi.$courses.find();
    } catch (error) {
      this.error = error;
    }
  },
};
</script>
