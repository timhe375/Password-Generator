<template>
  <header>
    <h1>Password Generator</h1>
  </header>
  <body>
    <section>
      <p>genereriertes PW</p>
      <button>Copy to Clipboard</button>
      <p>Password was succesfully copied to your clipboard!</p>
    </section>
  </body>
  <form onsubmit="return false">
    <div>
      <p>Choose your character set:</p>
      <article>
        <section class="lowercase">
          <input type="checkbox" id="pw-tolowercase" checked />
          <label for="pw-tolowercase">Lowercase</label>
        </section>
        <section class="uppercase">
          <input type="checkbox" id="pw-touppercase" checked />
          <label for="pw-touppercase">Uppercase</label>
        </section>
        <section class="numbers">
          <input type="checkbox" id="pw-numbers" checked />
          <label for="pw-numbers">Numbers</label>
        </section>
        <section class="special">
          <input type="checkbox" id="pw-speacialchar" checked />
          <label for="pw-speacialchar">Symbols</label>
        </section>
      </article>
    </div>
    <section class="slider">
      <label for="pw-length">Password Lenght:</label><br />
      <input type="range" id="pw-length" min="8" max="35" step="1" />
    </section>
  </form>
</template>

<script>
export default {
  name: "PasswordGenerator",
  props: {
    msg: String,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
