<template>
  <div class="home">
    <h1>Home</h1>
    <input type="text" v-model="search" />
    <p>search term - {{ search }}</p>
    <div v-for="name in matchingNames" :key="name">{{ name }}</div>
    <button @click="stopEffect">Stop Watch Effect</button>
  </div>
</template>

<script>
import { computed, ref, watchEffect } from "vue";
// @ is an alias to /src
export default {
  name: "Home",
  setup() {
    const search = ref("");
    const names = ref(["John", "Jane"]);

    const stopEffect = watchEffect(() => {
      console.log("watch effect", search.value);
    });

    const matchingNames = computed(() => {
      return names.value.filter((name) => name.includes(search.value));
    });

    return {
      names,
      search,
      matchingNames,
      stopEffect,
    };
  },
};
</script>
