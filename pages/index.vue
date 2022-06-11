<template>
  <Mountains :mountains="mountains" />
</template>

<script>
export default {
  name: "IndexPage",
  async asyncData(ctx) {
    console.log("========", ctx);
    const res = await fetch("https://api.nuxtjs.dev/mountains");
    const mountains = await res.json();
    console.log("mountains: ", mountains);
    return { mountains };
  },
};
</script>
