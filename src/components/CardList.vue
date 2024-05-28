<script>
export default {
  props: ['card', 'archetype'],
  data() {
    return {};
  },
  methods: {
    getImage(nomefile) {
      return new URL(`../assets/${nomefile}`, import.meta.url);
    },
    test() {
      // console.log(this.card.archetype);
      // console.log(this.archetype);
    },
  },
  mounted() {
    this.test();
  },
};
</script>

<template>
  <div v-show="this.card.archetype == this.archetype" class="card">
    <img :src="this.card.card_images[0].image_url" alt="" />
    <h2>{{ this.card.name }}</h2>
    <div class="type">{{ this.card.archetype }}</div>
  </div>
</template>

<style scoped>
.card {
  width: 18%;
  background-color: rgb(162, 162, 162);
}

img {
  width: 100%;
}

h2 {
  text-align: center;
}

.type {
  font-size: 20px;
  color: black;
  text-align: center;
}
</style>
