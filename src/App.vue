<template>
  <header>
    <router-link to="/">
      <h1>Movies</h1>
    </router-link>
  </header>
  <main>
    <router-view/>
  </main>
</template>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Fira Sans', sans-serif;

  &::selection {
    background: transparentize($color: #4288, $amount: 0.5);
  }
}

body {
    background-color: rgb(217, 217, 217);
}

header {
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 10px 16px;
  background-color: rgb(170, 44, 44);
  box-shadow: 0px 0px 6px rgba(0, 0, 0, 0.2);
}

h1 {
  color: white;
  font-size: 28px;

  span {
   color: lightblue;
  }
}
</style>
