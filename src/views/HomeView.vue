<template>
  <div class="home">Home</div>
  <p ref="p">My name is {{ name }} and my age is {{ age }}</p>
  <button @click="handleClick">CLICK</button>
  <button @click="age++">CLICK TO ADD 1 TO AGE</button>
  <input type="text" v-model="name" />
</template>

<script>
import { ref } from "@vue/reactivity";
// @ is an alias to /src

export default {
  name: "HomeView",
  setup() {
    // in the setup function we can write regular JS
    // const p = ref(null);

    // We access the ref value using variableName.value
    const name = ref("Mario");

    const age = ref(41);

    const handleClick = () => {
      // This will update the name variable but the change won't be reflected in the template since we are using the Composition API.
      // In order to have reactie data we need to use REFS
      name.value = "Luigi";
      console.log(name);
    };

    // In order to have access to these variables in the template we need to return them inside of an object.
    // Keep in mind, this is different than using the data() function. The data inside the setup() function is NOT reactive. So if a the value of "name" changes it WILL NOT be reflected in the template.

    return { name, age, handleClick };
    // this is the same of writing return {name: name, age: age, handleClick : handleClick}
  },
};
</script>
