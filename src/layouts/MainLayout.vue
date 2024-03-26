<template>
  <q-layout view="hHh lpR fFf">
    <q-header elevated reveal class="bg-white text-primary" height-hint="98">
      <q-toolbar>
        <q-toolbar-title>
          <q-avatar>
            <img
              src="https://play-lh.googleusercontent.com/4QdiqfgqEoIdHAWmMe6m9VKVhfw94E8zUluQ-KmtAwEnUijT2Tbb6lApzyqbQlAKH88"
            />
          </q-avatar>
          Komijut
        </q-toolbar-title>
      </q-toolbar>

      <q-tabs align="center">
        <q-route-tab to="/" label="Home" />
        <q-route-tab to="/search" label="Search" />
        <q-route-tab to="/genre" label="Genre" />
      </q-tabs>
    </q-header>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script setup lang="ts">
defineOptions({
  name: 'MainLayout',
});
</script>
