<template>
  <div class="home">
    <h1>Home</h1>
    <h2>REFS</h2>
    <p>{{ ninjaOne.name }} - {{ ninjaOne.age }}</p>
    <button @click="updateNinjaOne">Update Ninja 1</button>

    <h2>REACTIVE</h2>
    <p>{{ ninjaTwo.name }} - {{ ninjaTwo.age }}</p>
    <button @click="updateNinjaTwo">Update Ninja 2</button>

    <p>nameTwo is: {{ nameTwo }}</p>
  </div>
</template>

<script>
import { ref, reactive } from "@vue/reactivity";
// @ is an alias to /src

export default {
  name: "HomeView",
  setup() {
    // §We have created a REF with an object as a value
    const ninjaOne = ref({ name: "Mario", age: 89 });
    const updateNinjaOne = () => {
      ninjaOne.value.age = 41;
    };

    const ninjaTwo = reactive({ name: "Yoshi", age: 66 });
    const updateNinjaTwo = () => {
      //This is one of the main differences of using REFS vs REACTIVE.
      // When we use REACTIVE we don't need to type ninjaTwo.value.age in order to access the property. We can directly type ninjaTwo.age
      ninjaTwo.age = 21;
    };

    // There are though drawbacks to using REACTIVE instead of REFS.
    // One of them is that we cannot use primitive values inside REACTIVE
    // So basically, JUST USE REFS AND SAVE YOURSELF TIME

    const nameOne = ref("Pristocchio");
    const nameTwo = reactive("Osvaldo");

    // Since we return the ninjaOne ref object, we can then have access to it in the template by simply calling the value we need, like ninjaOne.name (instead of ninjaOne.value.name)
    return { ninjaOne, updateNinjaOne, ninjaTwo, updateNinjaTwo, nameTwo };
    // this is the same of writing return {name: name, age: age, handleClick : handleClick}
  },
};
</script>
