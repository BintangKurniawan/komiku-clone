<template>
  <q-page class="flex justify-center gap-4 m-6 flex-row">
    <div v-for="item in data" :key="item">
      <card-manga
        :title="item.title"
        :thumbnail="item.image"
        :desc="item.desc"
        :endpoint="item.endpoint"
      />
    </div>
  </q-page>
</template>

<!-- eslint-disable @typescript-eslint/no-explicit-any -->
<script lang="ts">
import { api } from 'src/boot/axios';
import CardManga from 'src/components/CardManga.vue';
export default {
  mounted() {
    this.getData();
  },
  components: { CardManga },
  data() {
    return {
      data: [] as any,
    };
  },
  methods: {
    async getData() {
      await api
        .get('/api/comic/recommended/page/1')
        .then((res) => {
          this.data = res.data.data;
        })
        .catch((err) => console.log(err));
    },
  },
};
</script>
