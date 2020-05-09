<template>
  <div>
    <encabezado-component></encabezado-component>
    <div class="container">
      <div id="flow">
        <span class="flow-1"></span>
        <span class="flow-2"></span>
        <span class="flow-3"></span>
      </div>
      <div class="section">
        <div class="box">
          <div class="field has-addons">
            <div class="control is-expanded">
              <input
                v-model="search"
                v-on:keyup.enter="searchData()"
                class="input has-text-centered"
                type="search"
                placeholder="Escribe tu búsqueda"
              >
            </div>
            <div class="control">
              <a v-on:click="searchData()" class="button is-primary">Buscar</a>
            </div>
          </div>
        </div>

        <!-- Staff -->
        <div class="row columns is-multiline">
          <personaje-component
            v-for="character of characters"
            v-bind:key="character.id"
            v-bind:character="character"
          ></personaje-component>
        </div>
        <!-- End Staff -->
      </div>
      <nav class="pagination" role="navigation" aria-label="pagination">
        <a class="pagination-previous" v-on:click="changePage('anterior')">Anterior</a>
        <!-- <ul>
        <li>-->
        <a class="pagination-link is-current">{{page}}</a>
        <!-- </li>
        </ul>-->
        <a class="pagination-next" v-on:click="changePage('siguiente')">Siguiente</a>
      </nav>
    </div>
  </div>
</template>

<script>
import axios from "axios";

import EncabezadoComponent from "./components/EncabezadoComponent.vue";
import PersonajeComponent from "./components/PersonajeComponent.vue";

export default {
  components: {
    EncabezadoComponent: EncabezadoComponent,
    PersonajeComponent: PersonajeComponent
  },
  data() {
    return {
      characters: [],
      page: 1,
      pages: 1,
      search: ""
    };
  },
  created: function() {
    this.fetch();
  },
  methods: {
    fetch() {
      console.log("me ejecuté");

      axios
        .get("https://rickandmortyapi.com/api/character/", {
          params: {
            page: this.page,
            name: this.search
          }
        })
        .then(res => {
          this.characters = res.data.results;
          this.pages = res.info.pages;
          console.log(this.characters);
        })
        .catch(err => {
          console.log(err);
        });
    },
    changePage(numpage) {
      if (numpage === "anterior") {
        this.page = this.page - 1;
      }
      if (numpage === "siguiente") {
        this.page = this.page + 1;
      }
      if (this.page <= 0) {
        this.page = 1;
      }

      this.fetch();
    },
    searchData() {
      this.page = 1;
      console.log(this.search);
      this.fetch();
    }
  }
};
</script>


