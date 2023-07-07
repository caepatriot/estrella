<template>
  <div class="section">
    <svg ref="scrollClaude" width="100" height="100" viewBox="0 0 24 24">
      <path
        d="M21,9H15V22H13V16H11V22H9V9H3V7H21M12,2A2,2 0 0,1 14,4A2,2 0 0,1 12,6C10.89,6 10,5.1 10,4C10,2.89 10.89,2 12,2Z"
      />
    </svg>
  </div>
  <div class="section"></div>
  <div class="section"></div>
  <div class="section"></div>
</template>

<style lang="css" scoped>
.section {
  position: relative;
  height: 100vh;
  width: 100vw;
}

.section:nth-of-type(1) {
  background-image: url("https://img.freepik.com/free-photo/beautiful-milky-way-night-sky_53876-139825.jpg?w=1060&t=st=1688724330~exp=1688724930~hmac=16fb9bbb2c6fd1f962815da46bab14c00c87109d3c6909937b3c51d7e3cc4c7b");
  background-repeat: no-repeat;
  background-attachment: fixed;
  background-position: center;
  background-size: 100%;

  height: 500vh;
}

svg {
  position: sticky;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  margin-top: -50px;
  margin-left: -50px;

  animation: rotate 1s linear infinite;
  animation-play-state: paused;
  animation-delay: calc(var(--scroll) * -1s);

  animation-iteration-count: 1;
  animation-fill-mode: both;
}

@keyframes rotate {
  to {
    transform: rotate(360deg);
  }
}

.section:nth-of-type(2) {
  background-image: url("https://images.pexels.com/photos/255379/pexels-photo-255379.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2");
  background-repeat: no-repeat;
  background-attachment: fixed;
  background-position: center;
  background-size: 100%;
  /* transform: skew(6deg) rotate(6deg); */
}

.section:nth-of-type(3) {
  background-image: url("https://images.pexels.com/photos/259915/pexels-photo-259915.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2");
  background-repeat: no-repeat;
  background-attachment: fixed;
  background-position: center;
  background-size: 100%;
}
.section:nth-child(odd) {
  background-color: red;
}
.section:nth-child(even) {
  background-color: #2c3e50;
}
</style>

<script>
// @ is an alias to /src
// import HelloWorld from "@/components/HelloWorld.vue";

export default {
  name: "HomeView",
  components: {},
  data: () => ({
    heroImage: require("@/assets/logo.jpg"),
    scrollPosition: 0,
  }),
  mounted() {
    window.addEventListener("scroll", this.updateScrollProperty, false);
    this.canvas = this.$refs.scrollClaude;
  },
  beforeUnmount() {
    window.removeEventListener("scroll", this.updateScrollProperty, false);
  },
  methods: {
    handleScroll() {
      this.scrollPosition = window.scrollY;
    },
  },
};
</script>
