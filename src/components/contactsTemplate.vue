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
               :class="{'contacts-row-list__item_active' : active === contact.id}"
          >
            <div class="contacts-row"
                 @click="selectedContact(contact); active = contact.id"
            >
              <div class="contacts-row__img">
                <img src="../assets/images/person-placeholder.jpg" alt="">
              </div>
              <div class="contacts-row__text">
                {{ contact.fullName }}
              </div>
              <div class="contacts-row__img">
                <img src="../assets/images/arrow-right.png" alt="">
              </div>
              <div class="contacts-row__img contacts-row__img_delete"
                   @click="deleteContact(contact.id)"
              >
                <img src="../assets/images/delete-icon.png" alt="">
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
          fullName: 'Dmitry Verteyko',
          photo: '',
          email: 'verteyko1990@gmail.com',
          phone: '+375 44 555 55 55',
          workPhone: '+780 29 434 44 44',
          address: 'Mazurova street 117 fl.123',
          notes: 'frontend',
        },
        {
          id: 2,
          fullName: 'Artur Frolov',
          photo: '',
          email: 'wertey@gmail.com',
          phone: '+375 44 111 11 55',
          workPhone: '+780 29 123 12 22',
          address: 'Golovatskogo 117 fl.23',
          notes: 'designer UX/UI',
        },
        {
          id: 3,
          fullName: 'Helena Beizerova',
          photo: '',
          email: 'test@gmail.com',
          phone: '+375 44 333 33 33',
          workPhone: '+780 29 444 44 44',
          address: 'Lenina 44 fl.133',
          notes: 'backend',
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
    deleteContact(id) {
      this.contacts = this.contacts.filter((contact) => contact.id !== id);
    },
    selectedContact(contact) {
      this.$emit('showInfoSelectedContact', contact);
    },
    addNewContact(fullName) {
      const newContact = {
        fullName,
        id: this.contacts.length + 1,
        email: '',
        phone: '',
        workPhone: '',
        notes: '',
        address: '',
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
          cursor: pointer;
          transition: opacity .15s ease-in;
          &:hover {
            opacity: .8;
          }
        }
      }

      &__text {
        width: 80%;
      }
    }
  }
</style>
