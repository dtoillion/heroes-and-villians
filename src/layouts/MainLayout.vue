<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar class="bg-dark" style="height: 60px;">
        <q-toolbar-title>
          {{ $t('appTitle') }}
        </q-toolbar-title>
        <q-btn
          flat
          dense
          round
          icon="settings"
          aria-label="Menu"
          @click="drawerOpen = !drawerOpen"
        />
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="drawerOpen"
      show-if-above
      :width="200"
      :breakpoint="400"
      side="right"
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
            <q-item-label>{{ $t('darkModeToggleTitle') }}</q-item-label>
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
      drawerOpen: false,
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
