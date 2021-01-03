<template>
  <div id="app">
    <!--debut menu vuematerial-->
    <md-menu md-direction="bottom-end" :mdCloseOnClick="closeOnClick" :mdCloseOnSelect="closeOnSelect">
      <md-button class="md-raised md-primary" md-menu-trigger>MENU</md-button>

      <md-menu-content>
        <md-menu-item><router-link to="/"><md-button>Home</md-button></router-link></md-menu-item>
        <md-menu-item
          ><router-link to="/hello"><md-button>HelloWorld</md-button></router-link></md-menu-item
        >
        
      </md-menu-content>
    </md-menu>
    <!--fin menu vuematerial-->
    <!--
    <router-link to="/">[Home]</router-link>
    <router-link to="/restaurant">[Détails d'un Restaurant]</router-link>
    <router-link to="/hello">[HelloWorld]</router-link>
-->
    <router-view></router-view>
  </div>
</template>

<script>
export default {
  name: "App",
  components: {},
  data() {
    return {
      closeOnClick: true,
    };
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
