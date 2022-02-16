<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-toolbar-title class="absolute-center"> {{ title }} </q-toolbar-title>
      </q-toolbar>
    </q-header>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
// import EssentialLink from "components/EssentialLink.vue";

import { defineComponent, ref, computed } from "vue";
import { useRoute } from "vue-router";

export default defineComponent({
  name: "MainLayout",

  components: {
    // EssentialLink,
  },

  setup() {
    const route = useRoute();

    const leftDrawerOpen = ref(false);

    const title = computed(() => {
      let currentPath = route.fullPath;
      let theTitle = "";

      if (currentPath == "/") {
        theTitle = "chat app";
      } else if (currentPath == "/auth") {
        theTitle = "login";
      } else if (currentPath == "/chat") {
        theTitle = "chat";
      }
      return theTitle;
    });

    return {
      title,
    };
  },
});
</script>
