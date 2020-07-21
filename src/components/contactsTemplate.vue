<template>
    <div class="contacts">
      <div class="contacts-row">
        <input type="text"
               class="input"
               v-model="searchField"
        >
      </div>
      <div class="contacts-row">
        <div class="contacts-row-list">
          <div class="contacts-row-list__item"
               v-for="contact in filteredContacts"
               :key="contact.id"
               @click="selectedContact(contact); active = contact.id"
               :class="{'contacts-row-list__item_active' : active === contact.id}"
          >
            <div class="contacts-row">
              <div class="contacts-row__img">
                <img src="../assets/images/person-placeholder.jpg" alt="">
              </div>
              <div class="contacts-row__text">
                {{ contact.fullName }}
              </div>
              <div class="contacts-row__img">
                <img src="../assets/images/arrow-right.png" alt="">
              </div>
            </div>
          </div>
        </div>
      </div>
      <div class="contacts-row contacts-row_right">
        <div class="btn"
             @click="isVisibleModalContact = true"
        >New Contact</div>
      </div>
      <transition name="fade-el">
        <modalContactTemplate
          v-if="isVisibleModalContact"
          @closeModalContact="closeModalContact"
          @addNewContact="addNewContact"/>
      </transition>
    </div>
</template>

<script>
import modalContactTemplate from './modals/modalContactTemplate.vue';

export default {
  name: 'contactsTemplate',
  components: {
    modalContactTemplate,
  },
  data() {
    return {
      contacts: [
        {
          id: 1,
          fullName: 'Dmitry',
          photo: '',
        },
        {
          id: 2,
          fullName: 'Artur',
          photo: '',
        },
        {
          id: 3,
          fullName: 'Helena',
          photo: '',
        },
      ],
      searchField: '',
      isVisibleModalContact: false,
      active: -1,
    };
  },
  computed: {
    filteredContacts() {
      return this.contacts.filter((contact) => contact.fullName.match(this.searchField));
    },
  },
  methods: {
    selectedContact(contact) {
      this.$emit('showInfoSelectedContact', contact);
    },
    addNewContact(fullName) {
      const newContact = {
        fullName,
        id: this.contacts.length + 1,
      };
      this.contacts.push(newContact);
    },
    closeModalContact(data) {
      this.isVisibleModalContact = data;
    },
  },
};
</script>

<style scoped lang="scss">
  @import "src/assets/scss/variables";
  .contacts {
    &-row {
      display: flex;
      padding: 1vh;
      align-items: center;
      justify-content: flex-start;
      &-list {
        width: 100%;
        &__item {
          &_active {
            background: rgba($color-black, .2);
          }
        }
      }
      &_right {
        justify-content: flex-end;
        border-top: 1px solid rgba($color-black, .3);
      }
      &__img {
        margin-right: 1vh;
        img {
          max-width: 5vh;
          height: auto;
        }
      }
      &__text {
        width: 80%;
      }
    }
  }
</style>
