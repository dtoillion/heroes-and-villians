<template>
  <q-page padding>
    <div class="row justify-center">
      <div v-for="hero in heroes" :key="hero.id" class="col-6 col-md-2 q-pa-md">
        <SuperHero :hero="hero" />
      </div>
    </div>
  </q-page>
</template>

<script>
import SuperHero from 'components/SuperHero';

export default {
  name: 'SuperHeroesPage',
  data() {
    return {
      heroes: [],
    };
  },
  components: {
    SuperHero,
  },
  methods: {
    // TODO: Move the data model to the vuex store
    // TODO: pagination? infinite scroll? loading them all is too slow
    loadHero() {
      this.$q.loading.show();
      this.$axios.get('https://cdn.rawgit.com/akabab/superhero-api/0.2.0/api/all.json')
        .then((response) => {
          this.heroes = response.data;
          this.$q.loading.hide();
        })
        .catch(() => {
          this.$q.notify({
            color: 'negative',
            position: 'top',
            message: 'Loading failed',
            icon: 'report_problem',
          });
          this.$q.loading.hide();
        });
    },
  },
  beforeMount() {
    this.loadHero();
  },
};
</script>
