<template>
  <div id="app">
    <b-navbar class="mb-5" toggleable="sm" type="light" variant="light">
      <b-navbar-toggle target="nav-text-collapse"></b-navbar-toggle>

      <b-navbar-brand>RICK AND MORTY APP</b-navbar-brand>

      <b-collapse id="nav-text-collapse" is-nav>
        <b-navbar-nav>
          <b-nav-item href="#">Inicio</b-nav-item>
          <b-nav-item href="#" disabled>Buscar</b-nav-item>
          <b-nav-item href="#" disabled>Acerca de</b-nav-item>
          <b-nav-item href="#" disabled
            ><b-form inline>
              <b-form-input
                id="inline-form-input-name"
                class="mb-2 mr-sm-2 mb-sm-0"
                placeholder="Buscar"
              ></b-form-input> </b-form
          ></b-nav-item>
        </b-navbar-nav>
      </b-collapse>
    </b-navbar>
    <b-container>
      <b-row>
        <b-col cols="12" md="6" lg="4" v-for="(item, i) in data" :key="i">
          <b-card
            :title="item.name"
            :img-src="item.image"
            img-alt="Image"
            img-top
            tag="article"
            style="max-width: 20rem"
            class="mb-2"
          >
            <b-card-text> Status: {{ item.status }} </b-card-text>
            <b-card-text> Specie: {{ item.species }} </b-card-text>
            <b-card-text> Origin: {{ item.origin.name }} </b-card-text>

            <b-button href="#" variant="primary">Go somewhere</b-button>
          </b-card>
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>
<script lang="ts">
export default {
  name: "App",
  data() {
    return {
      data: [],
    };
  },
  methods: {
    async getData() {
      try {
        const response = await fetch(
          "https://rickandmortyapi.com/api/character"
        );
        const data = await response.json();
        this.data = data.results;
        console.log(this.data);
      } catch (error) {
        console.error(error);
      }
    },
  },
  created() {
    this.getData();
  },
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
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
</style>
