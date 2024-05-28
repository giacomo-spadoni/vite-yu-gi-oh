<script>
export default {
  data() {
    return {
      logo: 'Yugioh_anime_logo.webp',
    };
  },
  methods: {
    getImage(nomefile) {
      return new URL(`../assets/${nomefile}`, import.meta.url);
    },
  },
};
</script>

<template>
  <header>
    <img :src="getImage(logo)" alt="" />
    <h1>Yu-Gi-Oh Api</h1>
  </header>
</template>

<style scoped>
header {
  background-color: white;
  color: black;
  font-size: 16px;
  display: flex;
  align-items: center;
  height: 5rem;
}

img {
  width: 10rem;
  margin: 0 2rem;
}
</style>
