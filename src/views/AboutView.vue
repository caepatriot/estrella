<template>
  <div class="d-flex align-center flex-column">
    <ClientReviewer />
  </div>
</template>

<script>
// @ is an alias to /src
import ClientReviewer from "@/components/ClientReviewer.vue";

export default {
  name: "HomeView",
  components: {
    ClientReviewer,
  },
};
</script>
