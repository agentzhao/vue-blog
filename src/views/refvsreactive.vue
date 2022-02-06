<template>
  <div class="home">
    <h2>Refs</h2>
    <p>My name is {{ one.name }} and my age is {{ one.age }}</p>
    <button @click="updateRef">Update Ref</button>
    <input type="text" v-model="one.name" />

    <h2>Reactive</h2>
    <p>My name is {{ two.name }} and my age is {{ two.age }}</p>
    <button @click="updateReactive">Update Reactive</button>
  </div>
</template>

<script>
import { ref, reactive } from "vue";
// @ is an alias to /src
export default {
  name: "Home",
  setup() {
    const one = ref({ name: "John", age: 30 });
    const two = reactive({ name: "John", age: 30 });

    const updateRef = () => {
      one.value.name = "Luigi";
      one.value.age = 40;
    };
    const updateReactive = () => {
      two.name = "Luigi";
      two.age = 40;
    };

    return {
      one,
      two,
      updateRef,
      updateReactive,
    };
  },
};
</script>
