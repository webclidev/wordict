<template>
  <v-app>
    <v-content>
      <Wordict />
    </v-content>
  </v-app>
</template>

<script>
import Wordict from "./components/Wordict";

export default {
  name: "App",
  components: {
    Wordict
  }
};
</script>
