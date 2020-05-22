<template>
  <div class="flex flex-col min-h-screen">
    <pageHeader />
    <nuxt />
    <pageFooter />
  </div>
</template>

<script>
import pageHeader from "~/components/Header.vue";
import pageFooter from "~/components/Footer.vue";

export default {
  components: {
    pageHeader,
    pageFooter,
  },
  head: {
    meta: [
      { charset: "utf-8" },
      { name: "viewport", content: "width=device-width, initial-scale=1" },
    ],
  },
};
</script>
