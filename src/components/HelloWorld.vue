<template>
  <v-card>
      <h1 v-if="pagina === 1"> <Pagina1 /></h1>
      <h1 v-if="pagina === 2"> <Pagina2 /></h1>

  </v-card>

</template>

<script>
import Pagina1 from '@/components/pagina1.vue'
import Pagina2 from '@/components/pagina2.vue'
import AppBar from '@/layouts/default/AppBar.vue'



export default {
  components: {Pagina1, Pagina2, AppBar},
  data() {
    pagina: AppBar.pagina
    return {
      drawer: null,
    }
  },
}
</script>
