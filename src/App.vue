<template>
  <link
    rel="stylesheet"
    href="https://use.fontawesome.com/releases/v5.15.4/css/all.css"
    integrity="sha384-DyZ88mC6Up2uqS4h/KRgHuoeGwBcD4Ng9SiP4dIRy0EXTlnuz47vAwmeGwVChigm"
    crossorigin="anonymous"
  />
  <PasswordGenerator />
</template>

<script>
import PasswordGenerator from "./components/PasswordGenerator.vue";

export default {
  name: "App",
  components: {
    PasswordGenerator,
  },
};
</script>

<style>
@import url(https://fonts.googleapis.com/css?family=Arvo:regular,italic,700,700italic);
*,
*::before,
*::after {
  box-sizing: border-box;
  padding: 0;
  margin: 0;
}
:root {
  --color-dark: #0f0a0a;
  --color-light: #f5efed;
  --color-secondary: #2292a4;
  --color-success: #cbe896;
}
html {
  font-family: "Arvo";
  font-size: 20px;
}
h1 {
  padding: 1rem 0;
}
button {
  cursor: pointer;
  font-family: inherit;
}
body {
  text-align: center;
  background: var(--color-dark);
  color: var(--color-light);
  padding: 0.5rem;
  max-width: 700px;
  margin: auto;
}
</style>
