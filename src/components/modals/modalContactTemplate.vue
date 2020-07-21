<template>
    <div class="contact-new">
      <div class="contact-new__content">
        <input type="text" v-model="contact.fullName">
        <button @click="newContact">Add</button>
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
      width: 20%;
      height: 10vh;
      background: $color-white;
      box-shadow: -2px -1px 10px -4px rgba($color-white, .75);
      display: flex;
      align-items: center;
      justify-content: center;
      flex-direction: column;
    }
  }
</style>
