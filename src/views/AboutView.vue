<template>
  <div class="about">
    <h1>This is an about page</h1>
  </div>
  <signIn />
</template>

<script>
// @ is an alias to /src
import signIn from "@/components/signIn.vue";

export default {
  name: "HomeView",
  components: {
    signIn,
  },
};
</script>