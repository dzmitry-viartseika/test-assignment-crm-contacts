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
                <img src="../assets/images/person-placeholder.jpg" alt="">
              </div>
              <div class="contacts-row__text">
                {{ contact.firstName }}
              </div>
              <div class="contacts-row__img">
                <img src="../assets/images/arrow-right.png" alt="">
              </div>
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
      align-items: center;
      justify-content: flex-start;
      &-list {
        width: 100%;
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
