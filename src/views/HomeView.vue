<template>
  <HelloWorld />
  <div class="section"></div>
  <div class="section"></div>
  <div class="section"></div>
  <div class="section"></div>
</template>

<style lang="css" scoped>
.section {
  height: 100vh;
  width: 100vw;
}
.section:nth-child(odd) {
  background: red;
}
</style>

<script>
// @ is an alias to /src
import HelloWorld from "@/components/HelloWorld.vue";

export default {
  name: "HomeView",
  components: {
    HelloWorld,
  },
};
</script>
