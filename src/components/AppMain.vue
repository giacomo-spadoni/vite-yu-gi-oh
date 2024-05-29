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
      arche: [],
      archetype: [],
      allArchetype: '',
    };
  },
  methods: {
    getImage(nomefile) {
      return new URL(`../assets/${nomefile}`, import.meta.url);
    },
    createArchetype() {
      axios
        .get('https://db.ygoprodeck.com/api/v7/archetypes.php')
        .then((response) => {
          this.allArchetype = response.data;
          // console.log(this.allArchetype);
          for (let i = 0; i < this.allArchetype.length; i++) {
            this.arche.push(this.allArchetype[i].archetype_name);
            this.archetype.push(this.allArchetype[i].archetype_name);
          }
          // console.log(this.archetype);
          // console.log(this.arche);
        });
    },
  },
  mounted() {
    this.createArchetype();
  },
};
</script>

<template>
  <main>
    <section>
      <div class="select">
        <select v-model="archetype" name="archetype">
          <option v-for="(element, i) in arche" :value="element">
            {{ element }}
          </option>
        </select>
      </div>
      <div class="card-container">
        <CardList
          v-for="(carta, i) in store"
          :archetype="archetype"
          :card="carta"
        />
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
  width: 200px;
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
  padding: 2rem;
}
</style>
