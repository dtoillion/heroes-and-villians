<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar class="bg-dark">
        <q-btn
          flat
          dense
          round
          icon="settings"
          aria-label="Menu"
          @click="leftDrawerOpen = !leftDrawerOpen"
        />

        <q-toolbar-title>
          {{ $t('appTitle') }}
        </q-toolbar-title>

      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      :width="200"
      :breakpoint="400"
    >
      <q-list padding>
        <q-item-label header>
          {{ $t('settingsTitle') }}
        </q-item-label>
        <q-item tag="label" v-ripple>
          <LanguageSwitcher />
        </q-item>
        <q-item tag="label" v-ripple>
          <q-item-section>
            <q-item-label>Dark mode</q-item-label>
          </q-item-section>
          <q-item-section avatar>
            <q-toggle @input="toggleDarkMode()" v-model="darkMode" />
          </q-item-section>
        </q-item>
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import LanguageSwitcher from 'components/LanguageSwitcher';

export default {
  name: 'MainLayout',
  components: {
    LanguageSwitcher,
  },
  data() {
    return {
      leftDrawerOpen: false,
      darkMode: true,
    };
  },
  methods: {
    toggleDarkMode() {
      this.$q.dark.toggle();
    },
  },
};
</script>
