<template>
    <div class="header">
      <div class="header__logo">
        Spine Contacts
      </div>
    </div>
</template>

<script>
export default {
  name: 'headerTemplate',
};
</script>

<style scoped lang="scss">
  @import "src/assets/scss/variables";

  .header {
    display: flex;
    justify-content: flex-start;
    align-items: center;
    padding: 15px 40px;
    background: $color-black;
    width: 100%;

    &__logo {
      color: $color-white;
      font-size: 3vh;
    }
  }
</style>
