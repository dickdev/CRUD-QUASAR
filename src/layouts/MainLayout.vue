<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="toggleLeftDrawer"
        />

        <q-toolbar-title> Quasar App </q-toolbar-title>

        <div>Quasar v{{ $q.version }}</div>
      </q-toolbar>
    </q-header>

    <q-drawer v-model="leftDrawerOpen" show-if-above bordered>
      <q-list>
        <q-item-label header> Dashboard</q-item-label>

        <EssentialLink
          v-for="link in linksList"
          :key="link.title"
          v-bind="link"
        />
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script setup>
import { ref } from "vue";
import EssentialLink from "components/EssentialLink.vue";

defineOptions({
  name: "MainLayout",
});

const linksList = [
  {
    title: "My Tasks",
    caption: "List of unfinished tasks",
    icon: "task",
    route_name: "my-tasks",
  },
  {
    title: "Finished Tasks",
    caption: "List of finished tasks",
    icon: "check_circle_outline",
    route_name: "finished-tasks",
  },
  {
    title: "Deleted Tasks",
    caption: "List of deleted tasks",
    icon: "delete_outline",
    route_name: "deleted-tasks",
  },

  {
    title: "Permanent Deleted Tasks",
    caption: "List of permanent deleted tasks",
    icon: "delete_outline",
    route_name: "permanent-tasks",
  },

  // {
  //   title: "Docs",
  //   caption: "quasar.dev",
  //   icon: "school",
  //   link: "https://quasar.dev",
  // },
  // {
  //   title: "Github",
  //   caption: "github.com/quasarframework",
  //   icon: "code",
  //   link: "https://github.com/quasarframework",
  // },
  // {
  //   title: "Discord Chat Channel",
  //   caption: "chat.quasar.dev",
  //   icon: "chat",
  //   link: "https://chat.quasar.dev",
  // },
  // {
  //   title: "Forum",
  //   caption: "forum.quasar.dev",
  //   icon: "record_voice_over",
  //   link: "https://forum.quasar.dev",
  // },
  // {
  //   title: "Twitter",
  //   caption: "@quasarframework",
  //   icon: "rss_feed",
  //   link: "https://twitter.quasar.dev",
  // },
  // {
  //   title: "Facebook",
  //   caption: "@QuasarFramework",
  //   icon: "public",
  //   link: "https://facebook.quasar.dev",
  // },
  // {
  //   title: "Quasar Awesome",
  //   caption: "Community Quasar projects",
  //   icon: "favorite",
  //   link: "https://awesome.quasar.dev",
  // },
];

const leftDrawerOpen = ref(false);

function toggleLeftDrawer() {
  leftDrawerOpen.value = !leftDrawerOpen.value;
}
</script>
