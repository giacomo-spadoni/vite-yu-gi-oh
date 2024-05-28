<script>
import CardList from './CardList.vue';
import store from '../data/store.js';

export default {
  components: {
    CardList,
  },
  data() {
    return {
      store,
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
  <main>
    <section>
      <div class="select">
        <select name="" id="">
          <option value="alien">alien</option>
          <option value="beast">beast</option>
          <option value="dark">dark</option>
        </select>
      </div>
      <div class="card-container">
        <CardList v-for="(carta, i) in store" :card="store[i]" />
      </div>
    </section>
  </main>
</template>

<style scoped>
main {
  min-height: 50rem;
  width: 100%;
  background-color: rgb(54, 54, 54);
}

section {
  width: 1200px;
  margin: 0 auto;
}

select {
  width: 100px;
  font-size: 20px;
  margin-top: 1rem;
}

.card-container {
  background-color: rgb(114, 114, 114);
  width: 100%;
  margin-top: 1rem;
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
  /* align-items: baseline; */
  padding: 2rem;
}
</style>
