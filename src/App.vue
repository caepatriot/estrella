<template>
  <v-app id="app">
    <v-toolbar class="main-toolbar" density="compact" rounded="true">
      <v-app-bar-nav-icon></v-app-bar-nav-icon>

      <v-toolbar-title>Estrelush</v-toolbar-title>

      <v-spacer></v-spacer>
      <nav>
        <v-btn class="mx-3" to="/" density="compact">Button</v-btn>
        <v-btn class="mx-3" to="/about" density="compact">About</v-btn>
      </nav>

      <v-spacer></v-spacer>

      <v-btn icon>
        <v-icon>mdi-magnify</v-icon>
      </v-btn>

      <v-btn icon>
        <v-icon>mdi-heart</v-icon>
      </v-btn>

      <v-btn icon>
        <v-icon>mdi-dots-vertical</v-icon>
      </v-btn>
    </v-toolbar>

    <v-main>
      <router-view />
    </v-main>
  </v-app>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  background: #2c3e50;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.main-toolbar {
  position: fixed;
  margin: 20px;
  width: auto;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}
</style>
