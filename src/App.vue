<template>
  <div class="app-contacts">
    <header-template/>
    <main class="app-contacts-content">
        <div class="app-contacts-content-left">
          <contacts-template @showInfoSelectedContact="showInfoSelectedContact"/>
        </div>
        <div class="app-contacts-content-right">
          <info-contact-template :activeContact="activeContact"/>
        </div>
    </main>
  </div>
</template>

<script>
import headerTemplate from './components/headerTemplate.vue';
import contactsTemplate from './components/contactsTemplate.vue';
import infoContactTemplate from './components/infoContactTemplate.vue';

export default {
  name: 'App',
  data: () => ({
    activeContact: null,
  }),
  components: {
    headerTemplate,
    contactsTemplate,
    infoContactTemplate,
  },
  methods: {
    showInfoSelectedContact(data) {
      this.activeContact = data;
    },
  },
};
</script>

<style lang="scss">
  @import "assets/scss/styles";
  .app-contacts {

    &-content {
      display: flex;
      &-left {
        width: 40%;
        border: 1px solid rgba($color-black, .3);
        height: 100%;
      }
      &-right {
        width: 60%;
      }
    }
  }
</style>
