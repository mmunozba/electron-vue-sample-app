<script src="plugins/vuetify.ts"></script>
<script src="router/index.ts"></script>
<script src="menuHandler.ts"></script>
<template>
  <v-app>
    <v-navigation-drawer
      v-model="drawer"
      app
      dark
      src="https://cdn.vuetifyjs.com/images/backgrounds/bg-2.jpg"
      permanent
    >
      <v-list nav>
        <v-list-item
          v-for="route in routes"
          :key="route.title"
          link
          :to="route.path"
        >
          <v-list-item-icon>
            <v-icon>{{ route.icon }}</v-icon>
          </v-list-item-icon>

          <v-list-item-content>
            <v-list-item-title>{{ route.title }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-system-bar app color="primary" dark height="40" class="titlebar">
      <div class="d-flex align-center">
        <v-img
          alt="Vuetify Logo"
          class="shrink mr-3"
          contain
          src="https://cdn.vuetifyjs.com/images/logos/vuetify-logo-dark.png"
          transition="scale-transition"
          width="20"
        />

        Electron Vue Sample App
      </div>

      <v-spacer></v-spacer>
      <div class="menuButtonContainer">
        <v-icon @click="minimizeWindow()">mdi-window-minimize</v-icon>

        <v-icon @click="maximizeWindow()">mdi-window-maximize</v-icon>

        <v-icon @click="closeWindow()">mdi-window-close</v-icon>
      </div>
    </v-system-bar>

    <v-main>
      <router-view />
    </v-main>
  </v-app>
</template>

<script lang="ts">
import Vue from "vue";
import HelloWorld from "./components/HelloWorld.vue";

window.ipcRenderer.on('window-handler-reply', (event, arg) => {
  console.log("Received reply: " + arg); // prints "pong"
});

export default Vue.extend({
  name: "App",

  data: () => ({
    drawer: null,
    routes: [
      { title: "Home", icon: "mdi-view-dashboard", path: "/" },
      { title: "Todo", icon: "mdi-checkbox-marked-outline", path: "/todo" },
      { title: "About", icon: "mdi-help-box", path: "/about" }
    ]
  }),
  methods: {
    closeWindow() {
      window.ipcRenderer.send('window-handler', 'close-window')
    },
    minimizeWindow() {
      window.ipcRenderer.send('window-handler', 'minimize-window')
    },
    maximizeWindow() {
      window.ipcRenderer.send('window-handler', 'maximize-window')
    }
  }
});
</script>

<style>
.titlebar {
  -webkit-app-region: drag;
}
.menuButtonContainer {
  -webkit-app-region: no-drag;
}
::-webkit-scrollbar {
  display: none;
}
</style>
