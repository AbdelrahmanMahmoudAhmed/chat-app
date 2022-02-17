<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-btn
          @click="goBack"
          v-if="$route.fullPath.includes('/chat')"
          icon="arrow_back"
          label="back"
          flat
          dense
        />
        <q-toolbar-title class="absolute-center">
          {{ title }}
        </q-toolbar-title>
        <q-btn
          to="/auth"
          class="absolute-right q-pr-sm"
          no-caps
          icon="account_circle"
          label="login"
          flat
          dense
        />
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
import { useRouter, useRoute } from "vue-router";

export default defineComponent({
  name: "MainLayout",

  components: {
    // EssentialLink,
  },

  setup() {
    const route = useRoute();
    const router = useRouter();

    // const leftDrawerOpen = ref(false);
    const goBack = () => {
      router.go(-1);
    };

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
      goBack,
    };
  },
});
</script>
