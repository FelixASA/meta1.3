<template>
  <v-container>
    <v-app-bar color="primary" density="compact">
      <v-app-bar-nav-icon
        color="secundary"
        @click.stop="drawer = !drawer"
      ></v-app-bar-nav-icon>

      <v-app-bar-title>Opciones</v-app-bar-title>
    </v-app-bar>

    <v-navigation-drawer v-model="drawer" temporary>
      <v-list-item title="Felix Arredondo"></v-list-item>

      <v-divider></v-divider>

      <v-list density="compact" nav>
        <v-list-item
          prepend-icon="mdi-view-dashboard"
          title="Home"
          value="home"
          @click="pagina = 1"
        ></v-list-item>
        <v-list-item
          prepend-icon="mdi-table"
          title="Tabla"
          value="tabla"
          @click="pagina = 2"
        ></v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-main>
      <div class="d-flex justify-center align-center h-100"></div>
    </v-main>

    <v-card>
      <h1 v-if="pagina === 1"><Pagina1 /></h1>
      <h1 v-if="pagina === 2"><Pagina2 /></h1>
    </v-card>
  </v-container>
</template>

<script>
import Pagina1 from "@/components/pagina1.vue";
import Pagina2 from "@/components/pagina2.vue";

export default {
  components: { Pagina1, Pagina2 },
  data() {
    return {
      drawer: null,
      pagina: 1,
    };
  },
};
</script>
