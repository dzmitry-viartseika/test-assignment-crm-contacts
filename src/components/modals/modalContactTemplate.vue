<template>
    <div class="contact-new">
      <div class="contact-new__content">
        <input type="text" class="contact-new__content-input" autofocus v-model="contact.fullName">
        <button class="btn contact-new__btn" @click="newContact">Add</button>
      </div>
      <div class="contact-new__overlay"
           @click.prevent="clickOutSide(false)"
      ></div>
    </div>
</template>

<script>
export default {
  name: 'modalContactTemplate',
  data: () => ({
    contact: {
      fullName: '',
    },
  }),
  methods: {
    newContact() {
      this.$emit('addNewContact', this.contact.fullName);
      this.$emit('closeModalContact', false);
    },
    clickOutSide(data) {
      this.$emit('closeModalContact', data);
    },
  },
};
</script>

<style scoped lang="scss">
  @import "src/assets/scss/variables";
  .contact-new {
    width: 100%;
    height: 100%;
    &__btn {
      margin-top: 10px;
    }
    &__overlay {
      position: absolute;
      width: 100vw;
      height: 100vh;
      left: 0;
      top: 0;
      background: rgba($color-black, .2);
      z-index: 1;
    }
    &__content {
      position: absolute;
      left: 50%;
      top: 50%;
      transform: translate(-50%,-50%);
      z-index: 2;
      width: 30%;
      height: 20vh;
      background: $color-white;
      box-shadow: -2px -1px 10px -4px rgba($color-white, .75);
      display: flex;
      align-items: center;
      justify-content: center;
      flex-direction: column;
      padding: 5vh;
      &-input {
        height: 5vh;
        padding: 1vh;
      }
    }
  }
</style>
