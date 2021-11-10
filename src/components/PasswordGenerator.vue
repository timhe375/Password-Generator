<template>
  <header>
    <h1 class="title">Password Generator</h1>
  </header>
  <body>
    <section class="pw-result">
      <p id="generated-password">{{ generatedPassword }}</p>
      <button @click="copiedPassword">Copy to Clipboard</button>
      <p class="succes-generated-pw">
        Password was succesfully copied to your clipboard!
      </p>
    </section>
  </body>
  <form onsubmit="return false">
    <main class="pw-setcheck">
      <p>Choose your character set:</p>
      <article class="container">
        <section class="lowercase">
          <input type="checkbox" id="pw-tolowercase" checked />
          <label for="pw-tolowercase" class="container-category"
            >Lowercase</label
          >
        </section>
        <section class="uppercase">
          <input type="checkbox" id="pw-touppercase" />
          <label for="pw-touppercase" class="container-category"
            >Uppercase</label
          >
        </section>
        <section class="numbers">
          <input type="checkbox" id="pw-numbers" />
          <label for="pw-numbers" class="container-category">Numbers</label>
        </section>
        <section class="special">
          <input type="checkbox" id="pw-speacialchar" />
          <label for="pw-speacialchar" class="container-category"
            >Symbols</label
          >
        </section>
      </article>
    </main>
    <section class="slider">
      <label for="pw-length">Password Lenght:</label><br />
      <input
        type="range"
        id="pw-length"
        min="8"
        max="35"
        step="1"
        class="pw-length-slider"
        :value="value"
        @input="updateValue()"
      />
      <label for="pw-length" class="slider-value">{{ value }}</label>
    </section>
  </form>
</template>

<script>
export default {
  name: "PasswordGenerator",
  data() {
    return {
      value: 8,
      generatedPassword: "",
    };
  },

  props: {},
  methods: {
    updateValue() {
      this.value = document.getElementById("pw-length").value;
      return this.generatePassword(this.value);
    },
    generatePassword() {
      let length = this.value;
      let charSet =
        "0123456789abcdefghijklmnopqrstuvwxyz!@#$%^&*()ABCDEFGHIJKLMNOPQRSTUVWXYZ";
      this.generatedPassword = "";

      for (let i = 0; i < length; i++) {
        this.generatedPassword += charSet.charAt(
          Math.floor(Math.random() * charSet.length)
        );
      }
      return this.generatedPassword;
    },
  },
  mounted() {
    this.generatePassword();
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.title {
  font-size: 40px;
  text-transform: uppercase;
  letter-spacing: 0.2rem;
  color: var(--color-secondary);
}
input[type="range"] {
  -webkit-appearance: none;
  appearance: none;
  background-color: var(--color-light);
  height: 0.5rem;
  border-radius: 0.5rem;
}
.pw-result {
  margin: 2rem auto 3rem auto;
  height: 9.5rem;
}
.pw-result :first-child {
  background: rgba(255 255 255 / 0.1);
  padding: 1rem;
  border-radius: 0.1rem;
  word-wrap: break-word;
  margin: 1rem 0;
}
button {
  font-size: 1rem;
  background-color: var(--color-secondary);
  border: none;
  padding: 0.2rem 0.5rem;
  border-radius: 0.2rem;
}
.succes-generated-pw {
  background-color: var(--color-success);
  font-size: 1rem;
  color: var(--color-dark);
  width: 50%;
  margin: auto;
  margin-top: 2rem;
  padding: 1rem;
  border-radius: 0.2rem;
  opacity: 0;
  transition: opacity 0.5s;
  cursor: default;
  pointer-events: none;
}
.pw-setcheck {
  display: flex;
  flex-direction: column;
  gap: 2rem;
  margin: 1rem 0 2rem 0;
}
.container {
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  gap: 1rem;
}
.pw-setcheck input[type="checkbox"] {
  display: none;
}
.container-category {
  color: rgba(255 255 255 / 0.5);
  border: 2px solid rgba(255 255 255 / 0.5);
  padding: 0.5rem 0.5rem;
  border-radius: 0.5rem;
}
input[type="checkbox"]:checked + .container-category {
  background: var(--color-secondary);
  color: var(--color-light);
  border-color: var(--color-secondary);
}
.slider-value {
  display: inline-block;
  max-width: 2rem;
  margin-left: 0.5rem;
}
.pw-length-slider {
  width: 80%;
  max-width: 15rem;
}
</style>
