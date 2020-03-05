<template>
  <q-select
    v-model="lang"
    :options="langOptions"
    :label="$t('languageSwitcherLabel')"
    borderless
    emit-value
    map-options
    style="min-width: 100%"
  />
</template>

<script>
export default {
  name: 'LanguageSwitcher',
  data() {
    return {
      lang: this.$i18n.locale,
      langOptions: [
        { value: 'en-us', label: 'English' },
        { value: 'nl', label: 'Dutch' },
      ],
    };
  },
  watch: {
    lang(lang) {
      this.$i18n.locale = lang;
    },
  },
};
</script>
