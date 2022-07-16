<template>
  <div class="home">
    <h1>Home</h1>
    <p>{{ name }}</p>
  </div>
</template>

<script>
// @ is an alias to /src
import { computed, ref } from "@vue/runtime-core";

export default {
  name: "HomeView",
  setup() {
    const name = computed(() => {
      return "Ninja";
    });

    return { name };
  },
};
</script>
