<template>
  <div>
    <!-- <div id="nav"> -->
    <!--   <router-link to="/">Home</router-link> | -->
    <!--   <router-link to="/about">About</router-link> -->
    <!-- </div> -->
    <router-view />
  </div>
</template>
<script>
export default {
  setup() {},
};
</script>
<style>
@import url("https://fonts.googleapis.com/css2?family=Poppins:ital,wght@0,100;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,300&display=swap");
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Poppins", sans-serif;
}
:root {
  --color-primary: rgb(0, 100, 255);
  --color-background: rgba(0, 0, 0, 0.7);
}

body::-webkit-scrollbar {
  width: 0.8vw;
}
body::-webkit-scrollbar-thumb {
  background: var(--color-primary);
  border-radius: 0.8vw;
}
body::-webkit-scrollbar-track {
  background: rgba(0, 0, 0, 0.7);
}

@media screen and (max-width: 812px) {
  body::-webkit-scrollbar {
    width: 1.2vw;
  }
  body::-webkit-scrollbar-thumb {
    border-radius: 1.2vw;
  }
}

@media screen and (max-width: 500px) {
  body::-webkit-scrollbar {
    width: 2vw;
  }
  body::-webkit-scrollbar-thumb {
    border-radius: 2vw;
  }
}

@media screen and (max-width: 812px) {
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  box-sizing: border-box;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
