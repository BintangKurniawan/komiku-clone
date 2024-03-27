<template>
  <q-page class="flex gap-4 m-6 flex-col">
    <div class="flex gap-8 items-start">
      <q-img :src="img" width="300px" height="auto" />

      <div class="flex flex-col gap-4">
        <h4 class="text-2xl font-bold">{{ title }}</h4>
        <p>{{ genre }}</p>
        <div class="flex items-center gap-2">
          <Icon icon="mdi:people-check-outline" width="24" />
          <p>{{ rating }}</p>
        </div>
        <div class="flex items-center gap-2">
          <Icon icon="mdi:person-star-outline" width="24" />
          <p>{{ author }}</p>
        </div>
        <div class="flex items-center gap-2">
          <Icon icon="mdi:information-slab-circle-outline" width="24" />
          <p>{{ status }}</p>
        </div>
      </div>
    </div>
  </q-page>
</template>

<script lang="ts">
import { Icon } from '@iconify/vue';
import { api } from 'src/boot/axios';

export default {
  setup() {
    return {};
  },
  components: {
    Icon,
  },
  data() {
    return {
      img: '',
      title: '',
      genre: '',
      rating: '',
      author: '',
      status: '',
    };
  },
  mounted() {
    console.log('ambatukam');
    console.log(this.$route.params.title);
    this.getData();
  },
  methods: {
    async getData() {
      await api
        .get('/api/comic/info/manga/' + this.$route.params.title + '/')
        .then((res) => {
          console.log(res.data.data);
          this.img = res.data.data.thumbnail;
          this.title = res.data.data.title;
          this.rating = res.data.data.rating;
          for (let i = 0; i < res.data.data.genre.length; i++) {
            if (i != res.data.data.genre.length - 1) {
              this.genre += res.data.data.genre[i] + ', ';
            } else {
              this.genre += res.data.data.genre[i];
            }
          }
          this.author = res.data.data.author;
          this.status = res.data.data.status;
        })
        .catch((err) => {
          console.log(err);
        });
    },
  },
};
</script>

<style scoped></style>
