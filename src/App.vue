<template>
  <header>
    <router-link to="/">
      <h1>N<span>(Vue)</span>Movies</h1>
    </router-link>
  </header>
  <main>
    <router-view />
  </main>
</template>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: Avenir, system-ui, Roboto, sans-serif;

  &::selection {
    background: transparentize(#42b883, 0.5);
  }
}
body {
  background-color: #35495e;
}

a {
  text-decoration: none;
}

header {
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 10px 16px;
  background-color: #2c3d4e;
  box-shadow: 0 0 6px rgba(0, 0, 0, 0.1);
}

h1 {
  color: white;
  font-size: 28px;
  span {
    color: #42b883;
  }
}
</style>
