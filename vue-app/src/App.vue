<template>
  <nav>
    <router-link to="/">Home</router-link> |
    <router-link to="/about">About</router-link>
  </nav>
  <router-view/>
</template>

<style lang="scss">
button{
  border: none;
  outline: none;
  background-color: transparent;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
.lineNumbers span {
            counter-increment: linenumber;
            &::before {
                content: counter(linenumber);
                display: block;
                color: black;
              }
          }
.blockPreview{
    a{
      padding: 12px 16px;
      background-color: black;
      border-radius: 20px;
      color:white;
      width: fit-content;
      text-decoration: none;
      font-weight: 600;
      
    }
}
</style>
