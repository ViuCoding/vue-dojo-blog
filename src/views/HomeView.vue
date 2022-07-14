<template>
  <div class="home">Home</div>
  <p>My name is {{ name }} and my age is {{ age }}</p>
  <button @click="handleClick">CLICK</button>
</template>

<script>
// @ is an alias to /src

export default {
  name: "HomeView",
  setup() {
    // in the setup function we can write regular JS
    let name = "Mario";
    let age = 41;

    const handleClick = () => {
      console.log("You clicked me!");
    };

    // In order to have access to these variables in the template we need to return them inside of an object.
    // Keep in mind, this is different than using the data() function. The data inside the setup() function is NOT reactive. So if a the value of "name" changes it WILL NOT be reflected in the template.

    return { name, age, handleClick };
    // this is the same of writing return {name: name, age: age, handleClick : handleClick}
  },
};
</script>
