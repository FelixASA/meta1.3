<template>
  <v-container>
    <v-row justify="space-around">
      <v-card width="300">
        <v-img
          height="280"
          :src= 'url'
          cover
          class="text-white"
        >
        <template v-slot:placeholder>
          <v-row
            class="fill-height ma-0"
            align="center"
            justify="center"
          >
          <v-progress-circular
            indeterminate
            color="grey lighten-5"
          ></v-progress-circular>
        </v-row>
        </template>
          <v-toolbar
            color="rgba(0, 0, 0, 0)"
            theme="dark"
          >
            <template v-slot:prepend>
              <v-btn icon="$menu"></v-btn>
            </template>

            <v-toolbar-title class="text-h6">
              Messages
            </v-toolbar-title>

            <template v-slot:append>
              <v-btn icon="mdi-dots-vertical"></v-btn>
            </template>
          </v-toolbar>
        </v-img>

        <v-card-text>
          <div class="font-weight-bold ms-1 mb-2">
            Today
          </div>

          <v-timeline density="compact" align="start">
            <v-timeline-item
              v-for="message in messages"
              :key="message.time"
              :dot-color="message.color"
              size="x-small"
            >
              <div class="mb-4">
                <div class="font-weight-normal">
                  <strong>{{ message.from }}</strong> @{{ message.time }}
                </div>
                <div>{{ message.message }}</div>
              </div>
            </v-timeline-item>
          </v-timeline>
        </v-card-text>
        <v-card-actions>
          <v-btn @click="recargaImagen" :color='red'>
            Reload
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-row>
  </v-container>
</template>

<script setup>
  import { ref } from 'vue';
    const messages = ref ([]);
    const red = ref ('blue');
    const url = ref ("https://i1.sndcdn.com/artworks-FZYtcnfgLHJp52Q2-lEfruQ-t500x500.jpg");
    messages.value = [
        {
          from: 'You',
          message: `Let me do it for you.`,
          time: '10:42am',
          color: 'deep-purple-lighten-1',
        },
        {
          from: 'John Doe',
          message: 'We knowly do is for you...',
          time: '10:37am',
          color: 'green',
        },
        {
          from: 'You',
          message: 'Kermit',
          time: '9:47am',
          color: 'deep-purple-lighten-1',
        },
      ];

      async function recargaImagen() {
          red.value = 'red';
          console.log("Recargando imagen...");
          url.value = "";
          let r = await fetch("https://random.imagecdn.app/500/150");
          url.value = r.url;
          console.log(r);
        }

</script>