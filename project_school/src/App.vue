<template>
  <div id="app">
    <Nav></Nav>
    <div class="marginPrincipal">
      <router-view :key="$route.fullPath"></router-view>
    </div>
  </div>
</template>

<script>
import Nav from "./components/_nav/Nav";

export default {
  name: "App",
  components: {
    Nav,
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Montserrat:ital,wght@0,400;0,700;1,200&display=swap");

body {
  background-color: #eeee;
  font-family: "Montserrat", sans-serif;
  display: grid;
  justify-items: center;
}
body,
html {
  margin: 0;
  height: 100%;
}
.marginPrincipal {
  width: 50%;
  margin: auto;
}

#app {
  width: 100%;
}

.btn_Danger {
  font-size: 0.8em !important;
  background-color: #fa4430;
}

.btn {
  border: 1px solid black;
  padding: 10px 20px;
  cursor: pointer;
  color: white;
  font-weight: bold;
  font-size: 1.2em;
  border-radius: 5px;
  border-bottom: 3px solid black;
}

.btn:hover {
  text-shadow: 1px 1px 1px black;
  margin-top: 3px;
  border-bottom: 1px solid black;
}

table {
  margin: 0;
  padding: 0;
  list-style-type: none;
  width: 100%;
}

table tr td {
  padding: 20px;
  font-size: 1.3em;
  background-color: #e0edfe;
  margin-bottom: 2px;
  color: #3e5252;
}

table thead th {
  background-color: rgb(184, 208, 216) !important;
  font-size: 1.2em;
  padding: 10px 0px;
  text-align: center !important;
}

.colPequeno {
  width: 5%;
  text-align: right;
  background-color: rgb(125, 217, 245);
  font-weight: bold;
}
</style>
