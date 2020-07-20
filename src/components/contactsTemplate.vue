<template>
    <div class="contacts">
      <div class="contacts-row">
        <input type="text" class="input">
      </div>
      <div class="contacts-row">
        <div class="contacts-row-list">
          <div class="contacts-row-list__item"
               v-for="contact in contacts"
               :key="contact.id"
          >
            <div class="contacts-row">
              <div class="contacts-row__img">
                x
              </div>
              <div class="contacts-row__text">
                {{ contact.firstName }}
              </div>
              <i>'>'</i>
            </div>
          </div>
        </div>
      </div>
      <div class="contacts-row contacts-row_right">
        <div class="btn">New Contact</div>
      </div>
    </div>
</template>

<script>
export default {
  name: 'contactsTemplate',
  data() {
    return {
      contacts: [
        {
          id: 1,
          firstName: 'wertey',
          lastName: 'wewqeqweq',
          photo: '',
        },
        {
          id: 2,
          firstName: 'wertey 2',
          lastName: 'wewqeqweq',
          photo: '',
        },
        {
          id: 3,
          firstName: 'wertey 3',
          lastName: 'wewqeqweq',
          photo: '',
        },
      ],
    };
  },
};
</script>

<style scoped lang="scss">
  @import "src/assets/scss/variables";
  .contacts {
    &-row {
      display: flex;
      padding: 1vh;
      &_right {
        justify-content: flex-end;
        border-top: 1px solid rgba($color-black, .3);
      }
    }
  }
</style>
