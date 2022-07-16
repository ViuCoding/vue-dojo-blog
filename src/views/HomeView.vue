<template>
  <div class="home">
    <h1>Home</h1>
    <input type="text" v-model="search" />
    <p>Search term: {{ search }}</p>
    <div v-for="name in matchingNames" :key="name">{{ name }}</div>
  </div>
</template>

<script>
// @ is an alias to /src
import { computed, ref } from "@vue/runtime-core";

export default {
  name: "HomeView",
  setup() {
    const names = ref(["mario", "luigi", "yoshi", "george", "kramer", "bowser", "frenchie"]);
    const search = ref("");

    const matchingNames = computed(() => {
      // Call back funtion for each item in the names array, and it returns true if the search value is included in the array. If not it will be filtered out
      return names.value.filter(item => item.includes(search.value))
    })

    return { names, search,matchingNames };
  },
};
</script>
