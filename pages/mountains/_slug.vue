<template>
  <div class="max-w-[1000px] mx-auto p-10">
    <n-link to="/">
      <button class="bg-green-500 text-gray-100 px-5 rounded">Back</button>
    </n-link>
    <p v-if="$fetchState.pending" class="loading text-green-500 mt-10">
      <span>Loding.....</span>
    </p>
    <p v-else-if="$fetchState.error" class="text-red-500 mt-10">
      Error while fetching mountains 🤬
    </p>
    <article class="mt-5" v-else>
      <section>
        <img :src="mountain.image" :alt="mountain.title" />
        <h1 class="text-lg text-green-500 py-4">{{ mountain.title }}</h1>
        <p class="text-gray-700 px-4 border-l-2">
          {{ mountain.description }}
        </p>

        <p class="mt-5 text-gray-500 capitalize">
          height: {{ mountain.height }}
        </p>
        <p class="text-gray-500 capitalize mt-4">
          Continent: {{ mountain.continent }}
        </p>
        <p class="text-gray-500 capitalize mt-4">
          countries:
          <span
            class="bg-green-500 text-sm text-gray-100 p-1 mx-1 rounded"
            v-for="(country, idx) in mountain.countries"
            :key="idx"
            >{{ country }}</span
          >
        </p>
      </section>
    </article>
  </div>
</template>

<script>
export default {
  data: function () {
    return {
      mountain: {},
    };
  },
  async fetch() {
    let res = await fetch(
      `https://api.nuxtjs.dev/mountains/${this.$route.params.slug}`
    );
    this.mountain = await res.json();
    console.log("mountain: ", this.mountain);
  },
};
</script>

<style></style>
