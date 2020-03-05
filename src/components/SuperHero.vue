<template>
  <div>
    <q-img
      transition="slide-right"
      :src="hero.images.lg"
      ratio="1"
      class="rounded-borders shadow-5"
      style="cursor: pointer;"
      @click="modalOpen = true"
    >
      <div class="absolute-bottom text-center text-body1">
        {{ hero.name }}
      </div>
      <template v-slot:loading>
        <q-skeleton height="180px" width="180px" />
      </template>
    </q-img>
    <q-dialog v-model="modalOpen">
      <q-card>
        <q-item>
          <q-item-section avatar>
            <q-avatar>
              <img :src="hero.images.lg">
            </q-avatar>
          </q-item-section>
          <q-item-section>
            <q-item-label>{{ hero.name }}</q-item-label>
            <q-item-label caption>
              {{ hero.biography.publisher }}
            </q-item-label>
          </q-item-section>
          <q-item-section avatar>
            <q-btn icon="close" flat round dense v-close-popup />
          </q-item-section>
        </q-item>

        <q-separator />

        <q-card-section horizontal>
          <q-card-section>
            <q-list>
              <!-- TODO: Styles for list and loop through arrays -->
              <!-- TODO: Dutch translations for labels -->
              <q-item>
                {{ $t('biographyFullNameLabel') }}: {{ hero.biography.fullName }}
              </q-item>
              <q-item>
                {{ $t('biographyFirstAppearanceLabel') }}: {{ hero.biography.firstAppearance }}
              </q-item>
              <q-item>
                {{ $t('biographyAlterEgosLabel') }}: {{ hero.biography.alterEgos }}
              </q-item>
              <q-item>
                {{ $t('biographyAliasesLabel') }}: {{ hero.biography.aliases }}
              </q-item>
              <q-item>
                {{ $t('biographyPlaceOfBirthLabel') }}: {{ hero.biography.placeOfBirth }}
              </q-item>
              <q-item>
                {{ $t('biographyAlignmentLabel') }}: {{ hero.biography.alignment }}
              </q-item>
            </q-list>
          </q-card-section>
        </q-card-section>
      </q-card>
    </q-dialog>
  </div>
</template>

<script>
export default {
  name: 'SuperHero',
  props: [
    'hero',
  ],
  data() {
    return {
      modalOpen: false,
    };
  },
};
</script>
