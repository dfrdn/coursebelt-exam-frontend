<template>
  <div>
    <div v-if="error">
      {{ error }}
    </div>
    <div
      class="m-6 grid grid-cols-1 sm:grid-cols-3 md:grid-cols-3 lg:grid-cols-3 xl:grid-cols-3 gap-4 mt-8"
      v-else
    >
      <div
        v-for="course in courses"
        :key="course.id"
        class="border rounded-lg bg-gray-100 hover:shadow-lg shadow-md flex flex-col transition-shadow duration-300"
      >
        <nuxt-link :to="`/courses/${course.slug}`">
          <div class="rounded-t-lg bg-white overflow-hidden h-48">
            <img class="object-contain" :src="course.image" />
          </div>
          <div class="pl-4 pr-4 pb-4 pt-4 rounded-lg">
            <h4
              class="mt-1 font-semibold text-base leading-tight truncate text-gray-700"
            >
              {{ course.title }}
            </h4>
            <div class="mt-1 text-sm text-gray-700">
              {{ course.description }}
            </div>
          </div>
        </nuxt-link>
      </div>
    </div>
  </div>
</template>

<script>
import { getStrapiMedia } from "~/utils/medias";

export default {
  props: {
    courses: Array,
    error: Object,
    storeUrl: String,
  },
  methods: {
    getStrapiMedia,
  },
};
</script>

<style></style>
