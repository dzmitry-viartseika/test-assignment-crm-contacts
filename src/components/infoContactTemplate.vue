<template>
    <div class="info-contact">
      {{ editing }}
      <div class="contacts-row">
        <button class="btn"
                @click="editing = !editing"
        >
          <template v-if="!editing">
            Edit Contact
          </template>
          <template v-else>
            Save Contact
          </template>
        </button>
      </div>
      <div class="info-contact-row">
        <label class="info-contact-row__label">
          Name
        </label>
        <div class="info-contact-row__text"
             v-if="!editing"
        >
          {{ activeContact.fullName }}
        </div>
        <div class="info-contact-row__text"
             v-else
        >
          <input type="text"
                 v-model="activeContact.fullName"
                 class="input">
        </div>
      </div>
      <div class="info-contact-row">
        <label class="info-contact-row__label">
          Email
        </label>
        <div class="info-contact-row__text"
             v-if="!editing"
        >
          verteyko2131@gmail.com
        </div>
        <div class="info-contact-row__text"
             v-else
        >
          <input type="text"
                 v-model="activeContact.email"
                 class="input">
        </div>
      </div>
      <div class="info-contact-row">
        <label class="info-contact-row__label">
          Mobile Phone
        </label>
        <div class="info-contact-row__text"
             v-if="!editing"
        >
          +375 (44) 555-55-55
        </div>
        <div class="info-contact-row__text"
             v-else
        >
          <input type="text"
                 v-model="activeContact.phone"
                 class="input">
        </div>
      </div>
      <div class="info-contact-row">
        <label class="info-contact-row__label">
          Work Number
        </label>
        <div class="info-contact-row__text"
             v-if="!editing"
        >
          +000 (00) 000-00-00
        </div>
        <div class="info-contact-row__text"
             v-else
        >
          <input type="text"
                 v-model="activeContact.workPhone"
                 class="input">
        </div>
      </div>
      <div class="info-contact-row">
        <label class="info-contact-row__label">
          Adress
        </label>
        <div class="info-contact-row__text"
             v-if="!editing"
        >
          Mazurova street 77 fl.101
        </div>
        <div class="info-contact-row__text"
             v-else
        >
          <input type="text"
                 v-model="activeContact.address"
                 class="input">
        </div>
      </div>
      <div class="info-contact-row">
        <label class="info-contact-row__label">
          Notes
        </label>
        <div class="info-contact-row__text"
             v-if="!editing"
        >
          Blank
        </div>
        <div class="info-contact-row__text"
             v-else
        >
          <textarea name="3" id="" cols="30" rows="10"
                    v-model="activeContact.notes"
          ></textarea>
        </div>
      </div>
    </div>
</template>

<script>
export default {
  name: 'infoContactTemplate',
  data: () => ({
    editing: false,
  }),
  props: {
    activeContact: {
      type: Object,
      default: () => {},
    },
  },
  computed: {
    contact() {
      return this.activeContact;
    },
  },
};
</script>

<style scoped lang="scss">
  @import "src/assets/scss/variables";
</style>
