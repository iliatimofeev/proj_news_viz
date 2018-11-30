<template>
  <v-app>
    <v-toolbar app>
      <v-toolbar-title class="headline">
        <span>ml4sg </span>
        <span class="font-weight-light">История новостей</span>
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn
        flat
        href="http://ods.ai/t"
        target="_blank"
      >
        <span class="mr-2">ods</span>
      </v-btn>
    </v-toolbar>

    <v-content >
      <Topics />
    </v-content>
  </v-app>
</template>

<script>
import Topics from "./components/Topics";

export default {
  name: "App",
  components: {
    Topics
  },
  data() {
    return {
      //
    };
  }
};
</script>
