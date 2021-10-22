<template>
  <div id="app">
    <header>
      <h3>Scheme</h3>
      <form id="theme-switcher">
        <div v-for="(theme, index) in themes" :key="index">
          <input
            checked
            type="radio"
            :id="theme.value"
            :name="theme.name"
            :value="theme.value"
            @change="setTheme(theme.value)"
            v-model="schema">
          <label :for="theme.value">
            {{ theme.value }}
          </label>
        </div>
      </form>
    </header>

    <main>
      <section>
        <div class="surface-samples">
          <div class="surface1 rad-shadow">1</div>
          <div class="surface2 rad-shadow">2</div>
          <div class="surface3 rad-shadow">3</div>
          <div class="surface4 rad-shadow">4</div>
          <div class="surface5 rad-shadow">5</div>
          <div class="surface6 rad-shadow">6</div>
        </div>
      </section>

      <section>
        <div class="text-samples">
          <h1 class="text1">
            <span class="swatch brand rad-shadow"></span>
            Brand
          </h1>
          <h1 class="text1">
            <span class="swatch text1 rad-shadow"></span>
            Text Color 1
          </h1>
          <h1 class="text2">
            <span class="swatch text2 rad-shadow"></span>
            Text Color 2
          </h1>
          <br>
          <p class="text1">
            Lorem ipsum dolor sit amet, consectetur adipiscing elit,
            sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.</p>
          <p class="text2">
            Ut enim ad minim veniam, quis nostrud
            exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.</p>
        </div>
      </section>
    </main>
  </div>
</template>

<script>

export default {
  name: 'App',
  data() {
    return {
      schema: null,
      themes: [
        {
          value: 'auto',
          name: 'theme',
        },
        {
          value: 'light',
          name: 'theme',
        },
        {
          value: 'dark',
          name: 'theme',
        },
        {
          value: 'dim',
          name: 'theme',
        },
      ],
    };
  },
  methods: {
    setTheme(theme) {
      const doc = document.firstElementChild;
      doc.setAttribute('color-scheme', theme);
    },
  },
};
</script>

<style lang="scss">
html,
body {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

#app {
  font-family: Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

* {
  box-sizing: border-box;
  margin: 0;

  /* brand foundation */
  --brand-hue: 212;
  --brand-saturation: 80%;
  --brand-lightness: 42%;

  /* light */
  --brand-light: hsl(var(--brand-hue) var(--brand-saturation) var(--brand-lightness));
  --text1-light: hsl(var(--brand-hue) var(--brand-saturation) 10%);
  --text2-light: hsl(var(--brand-hue) 30% 30%);
  --surface1-light: hsl(var(--brand-hue) 25% 90%);
  --surface2-light: hsl(var(--brand-hue) 20% 99%);
  --surface3-light: hsl(var(--brand-hue) 20% 92%);
  --surface4-light: hsl(var(--brand-hue) 20% 85%);
  --surface5-light: hsl(var(--brand-hue) 20% 82%);
  --surface6-light: hsl(var(--brand-hue) 20% 77%);
  --surface-shadow-light: var(--brand-hue) 10% 20%;
  --shadow-strength-light: .02;

  /* dark */
  --brand-dark: hsl(
      var(--brand-hue)
      calc(var(--brand-saturation) / 2)
      calc(var(--brand-lightness) / 1.5)
  );
  --text1-dark: hsl(var(--brand-hue) 15% 85%);
  --text2-dark: hsl(var(--brand-hue) 15% 55%);
  --surface1-dark: hsl(var(--brand-hue) 5% 7%);
  --surface2-dark: hsl(var(--brand-hue) 5% 11%);
  --surface3-dark: hsl(var(--brand-hue) 5%  20%);
  --surface4-dark: hsl(var(--brand-hue) 5% 25%);
  --surface5-dark: hsl(var(--brand-hue) 5% 30%);
  --surface6-dark: hsl(var(--brand-hue) 5% 35%);
  --surface-shadow-dark: var(--brand-hue) 50% 3%;
  --shadow-strength-dark: .8;

  /* dim */
  --brand-dim: hsl(
      var(--brand-hue)
      calc(var(--brand-saturation) / 1.25)
      calc(var(--brand-lightness) / 1.25)
  );
  --text1-dim: hsl(var(--brand-hue) 15% 75%);
  --text2-dim: hsl(var(--brand-hue) 10% 61%);
  --surface1-dim: hsl(var(--brand-hue) 10% 20%);
  --surface2-dim: hsl(var(--brand-hue) 10% 25%);
  --surface3-dim: hsl(var(--brand-hue) 5%  30%);
  --surface4-dim: hsl(var(--brand-hue) 5% 35%);
  --surface-shadow-dim: var(--brand-hue) 30% 13%;
  --shadow-strength-dim: .2;
}

:root {
  color-scheme: light;

  /* set defaults */
  --brand: var(--brand-light);
  --text1: var(--text1-light);
  --text2: var(--text2-light);
  --surface1: var(--surface1-light);
  --surface2: var(--surface2-light);
  --surface3: var(--surface3-light);
  --surface4: var(--surface4-light);
  --surface5: var(--surface5-light);
  --surface6: var(--surface6-light);
  --surface-shadow: var(--surface-shadow-light);
  --shadow-strength: var(--shadow-strength-light);
}

[color-scheme="light"] {
  color-scheme: light;

  --brand: var(--brand-light);
  --text1: var(--text1-light);
  --text2: var(--text2-light);
  --surface1: var(--surface1-light);
  --surface2: var(--surface2-light);
  --surface3: var(--surface3-light);
  --surface4: var(--surface4-light);
  --surface5: var(--surface5-light);
  --surface6: var(--surface6-light);
  --surface-shadow: var(--surface-shadow-light);
  --shadow-strength: var(--shadow-strength-light);
}

[color-scheme="dark"] {
  color-scheme: dark;

  --brand: var(--brand-dark);
  --text1: var(--text1-dark);
  --text2: var(--text2-dark);
  --surface1: var(--surface1-dark);
  --surface2: var(--surface2-dark);
  --surface3: var(--surface3-dark);
  --surface4: var(--surface4-dark);
  --surface5: var(--surface5-dark);
  --surface6: var(--surface6-dark);
  --surface-shadow: var(--surface-shadow-dark);
  --shadow-strength: var(--shadow-strength-dark);
}

[color-scheme="dim"] {
  color-scheme: dark;

  --brand: var(--brand-dim);
  --text1: var(--text1-dim);
  --text2: var(--text2-dim);
  --surface1: var(--surface1-dim);
  --surface2: var(--surface2-dim);
  --surface3: var(--surface3-dim);
  --surface4: var(--surface4-dim);
  --surface-shadow: var(--surface-shadow-dim);
  --shadow-strength: var(--shadow-strength-dim);
}

html {
  block-size: 100%;
  background-color: var(--surface1);
  color: var(--text1);
}

body {
  min-block-size: 100%;
  font-family: system-ui, sans-serif;
  padding: 5vmax;
  display: grid;
  place-content: center;
  gap: 5vmax;
}

main {
  display: flex;
  flex-flow: row wrap;
  align-items: center;
  align-content: center;
  justify-content: center;
  gap: 10vmax 10vmin;
}

section {
  display: grid;
  gap: 2.5vh;
}

h1 {
  font-weight: 100;
}

p {
  max-inline-size: 35ch;
  font-size: 1.25rem;
  line-height: 1.5;
}

header {
  display: inline-grid;
  gap: 1ch;
}

form {
  display: flex;
  gap: 2ch;
}

form > div {
  display: inline-flex;
  align-items: center;
  gap: .75ch;
}

.surface-samples {
  display: grid;
  --size: 20ch;
  grid-template-columns: var(--size) var(--size);
  grid-auto-rows: var(--size);
  gap: 2ch;
}

.surface-samples > * {
  border-radius: 1rem;
  display: grid;
  place-content: center;
  font-size: 3rem;
  font-weight: 200;
}

.text-samples {
  display: grid;
  gap: 1.5ch;
}

.text-samples > h1 {
  font-size: 2.5rem;
  display: inline-flex;
  align-items: center;
  gap: 1ch;
}

.brand {
  color: var(--brand);
  background-color: var(--brand);
}

.surface1 {
  background-color: var(--surface1);
  color: var(--text2);
}

.surface2 {
  background-color: var(--surface2);
  color: var(--text2);
}

.surface3 {
  background-color: var(--surface3);
  color: var(--text1);
}

.surface4 {
  background-color: var(--surface4);
  color: var(--text1);
}

.surface5 {
  background-color: var(--surface5);
  color: var(--text1);
}

.surface6 {
  background-color: var(--surface6);
  color: var(--text1);
}

.text1 {
  color: var(--text1);
  font-weight: 200;
}

.text2 {
  color: var(--text2);
}

.swatch {
  display: inline-block;
  flex-shrink: 0;
  inline-size: 1.5ch;
  block-size: 1.5ch;
  border-radius: 50%;
}

.swatch.text1 {
  background-color: var(--text1);
}

.swatch.text2 {
  background-color: var(--text2);
}

/*.rad-shadow {*/
/*  border: 1px solid hsl(var(--brand-hue) 10% 50% / 15%);*/
/*  box-shadow: 0 1rem .5rem -.5rem;*/
/*  box-shadow:*/
/*    0 2.8px 2.2px hsl(var(--surface-shadow) / calc(var(--shadow-strength) + .03)),*/
/*    0 6.7px 5.3px hsl(var(--surface-shadow) / calc(var(--shadow-strength) + .01)),*/
/*    0 12.5px 10px hsl(var(--surface-shadow) / calc(var(--shadow-strength) + .02)),*/
/*    0 22.3px 17.9px hsl(var(--surface-shadow) / calc(var(--shadow-strength) + .02)),*/
/*    0 41.8px 33.4px hsl(var(--surface-shadow) / calc(var(--shadow-strength) + .03)),*/
/*    0 100px 80px hsl(var(--surface-shadow) / var(--shadow-strength))*/
/*;*/
/*}*/
</style>
