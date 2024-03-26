<template>
  <q-page class="row items-center justify-evenly text-red-500">
    <p class="text-red-500">kknjt</p>
  </q-page>
</template>
<script lang="ts">
import { api } from 'src/boot/axios';

export default {
  mounted() {
    this.getData();
  },

  methods: {
    async getData() {
      await api
        .get('/list?filter=manga')
        .then((res) => console.log(res.data))
        .catch((err) => console.log(err));
    },
  },
};
</script>
