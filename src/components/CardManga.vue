<template>
  <q-card class="w-[210px]">
    <q-img
      :src="thumbnail"
      width="210px"
      height="auto"
      class="cursor-pointer"
      @click="goToDetail(endpoint)"
    >
      <div class="absolute-bottom">{{ title }}</div>
    </q-img>

    <q-card-section>
      {{ desc }}
    </q-card-section>
  </q-card>
</template>

<!-- eslint-disable @typescript-eslint/no-explicit-any -->
<script lang="ts">
export default {
  setup() {
    return {};
  },
  props: {
    title: String,
    thumbnail: String,
    desc: String,
    endpoint: String,
  },
  methods: {
    goToDetail(endpoint: any) {
      this.$router.push(endpoint);
    },
  },
};
</script>

<style scoped></style>
