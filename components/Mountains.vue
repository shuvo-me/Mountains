<!-- Please remove this file from your project -->
<template>
  <div class="bg-white">
    <h4
      class="text-left py-11 text-xl text-green-500 max-w-[1000px] mx-auto pb-10"
    >
      Mountains
    </h4>
    <div class="cards grid grid-cols-3 gap-6 max-w-[1000px] mx-auto pb-10">
      <n-link
        :to="{ name: 'mountains-slug', params: { slug: mountain.slug } }"
        v-for="(mountain, idx) in mountains"
        :key="idx"
      >
        <div class="card max-w-[700px] border b mx-auto">
          <img :src="mountain.image" :alt="mountain.title" />
          <div>
            <h4>{{ mountain.title }}</h4>
          </div>
        </div>
      </n-link>
    </div>
  </div>
</template>

<script>
export default {
  name: "NuxtTutorial",
  props: {
    mountains: {
      type: Array,
      require: false,
    },
  },
};
</script>
