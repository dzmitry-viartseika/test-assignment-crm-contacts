<template>
    <div>
      <div class="info-contact" v-if="activeContact">
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
            <template v-if="activeContact.fullName !== ''">
              {{ activeContact.fullName }}
            </template>
            <template v-else>
              blank
            </template>
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
            <template v-if="activeContact.email !== ''">
              {{ activeContact.email }}
            </template>
            <template v-else>
              blank
            </template>
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
            <template v-if="activeContact.phone !== ''">
              {{ activeContact.phone }}
            </template>
            <template v-else>
              blank
            </template>
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
            <template v-if="activeContact.workPhone !== ''">
              {{ activeContact.workPhone }}
            </template>
            <template v-else>
              blank
            </template>
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
            <template v-if="activeContact.address !== ''">
              {{ activeContact.address }}
            </template>
            <template v-else>
              blank
            </template>
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
            <template v-if="activeContact.notes !== ''">
              {{ activeContact.notes }}
            </template>
            <template v-else>
              blank
            </template>
          </div>
          <div class="info-contact-row__text"
               v-else
          >
          <textarea name="3" id="" cols="30" rows="10"
                    v-model="activeContact.notes"
                    class="info-contact-row__textarea"
          ></textarea>
          </div>
        </div>
      </div>
      <div class="info-contact"
           v-else
      >
        <div class="info-contact__text">
          Select contact
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
  .info-contact {
    padding: 1vh;
    &-row {
      padding: 1vh;
      &__label {
        margin-bottom: 1vh;
        display: block;
        font-weight: bold;
      }
      &__textarea {
        width: 100%;
      }
    }
    &__text {
      font-size: 3vh;
      text-align: center;
    }
  }
</style>
