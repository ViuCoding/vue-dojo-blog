<template>
  <div class="home">Home</div>
  <p ref="p">My name is {{ name }} and my age is {{ age }}</p>
  <button @click="handleClick">CLICK</button>
</template>

<script>
import { ref } from "@vue/reactivity";
// @ is an alias to /src

export default {
  name: "HomeView",
  setup() {
    // in the setup function we can write regular JS
    const p = ref(null);

    let name = "Mario";
    let age = 41;

    const handleClick = () => {
      console.log("You clicked me!");
      console.log(p, p.value);
      p.value.classList.add("test");
      p.value.innerHTML = "Hello NINJASSSS!";
    };

    // In order to have access to these variables in the template we need to return them inside of an object.
    // Keep in mind, this is different than using the data() function. The data inside the setup() function is NOT reactive. So if a the value of "name" changes it WILL NOT be reflected in the template.

    return { name, age, handleClick, p };
    // this is the same of writing return {name: name, age: age, handleClick : handleClick}
  },
};
</script>
