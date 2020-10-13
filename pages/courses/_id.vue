<template>
  <div v-if="this.course !== null">
    <div
      class="m-6 grid grid-cols-1 sm:grid-cols-2 md:grid-cols-2 lg:grid-cols-2 xl:grid-cols-2 gap-4 mt-8"
    >
      <div class="rounded-t-lg pt-2 pb-2">
        <img :src="course.image" class="m-auto" />
      </div>
      <div class="w-full p-5 flex flex-col justify-end space-y-16">
        <div>
          <h4
            class="mt-1 font-semibold text-lg leading-tight truncate text-gray-700"
          >
            {{ course.title }} - P{{ course.price }}
          </h4>
          <div class="mt-1 text-gray-600">{{ course.description }}</div>
        </div>

        <button
          v-if="course.status === 'published'"
          class="snipcart-add-item mt-4 bg-white border border-gray-200 d hover:shadow-lg text-gray-700 font-semibold py-2 px-4 rounded shadow"
          :data-item-id="course.id"
          :data-item-price="course.price"
          :data-item-url="`${this.$route.fullPath}`"
          :data-item-description="course.description"
          :data-item-image="course.image"
          :data-item-name="course.title"
        >
          Add to cart
        </button>

        <div class="text-center mr-10 mb-1" v-else>
          <div
            class="p-2 bg-indigo-800 items-center text-indigo-100 leading-none lg:rounded-full flex lg:inline-flex"
            role="alert"
          >
            <span
              class="flex rounded-full bg-indigo-500 uppercase px-2 py-1 text-xs font-bold mr-3"
              >Coming soon...</span
            >
            <span class="font-semibold mr-2 text-left flex-auto"
              >This article is not available yet.</span
            >
          </div>
        </div>
      </div>
    </div>

    <div
      class="video-player-box"
      playsinline="true"
      v-video-player:myVideoPlayer="playerOptions"
    ></div>
    <h2 class="text-3xl">Curriculum</h2>
    <div v-for="module in course.modules" :key="module.title">
      <h2 class="text-2xl">{{ module.title }}</h2>
      <ol>
        <li v-for="topic in module.topics" :key="topic.title">
          {{ topic.title }}
        </li>
      </ol>
    </div>
  </div>

  <div v-else>
    {{ error }}
  </div>
</template>

<script>
import { getStrapiMedia } from "~/utils/medias";

export default {
  data() {
    return {
      course: null,
      error: null,
      playerOptions: {},
    };
  },
  async mounted() {
    document.addEventListener("snipcart.ready", () => {
      Snipcart.events.on("cart.confirm.error", (confirmError) => {
        console.log(confirmError);
      });
      Snipcart.events.on("cart.confirmed", (cartConfirmResponse) => {
        console.log(cartConfirmResponse);
      });
    });

    try {
      this.course = await this.$strapi.$courses.findOne(this.$route.params.id);
      this.playerOptions = {
        muted: true,
        language: "en",
        playbackRates: [0.7, 1.0, 1.5, 2.0],
        sources: [
          {
            type: "video/mp4",
            src: this.course.video_preview,
          },
        ],
      };
    } catch (error) {
      this.error = error;
    }
  },
  methods: {
    getStrapiMedia,
  },
};
</script>
