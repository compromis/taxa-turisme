<template>
    <div class="bob-title">
      <img src="@/assets/images/spongebob/title-bob.svg" alt="">
      <img class="face" src="@/assets/images/spongebob/colmenero.webp" alt="">
    </div>
</template>

<script>
  export default {

  }
</script>

<style lang="scss" scoped>
.bob-title {
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 4rem;
  padding: 6rem 3rem;
  background-image: url('../assets/images/spongebob/background.webp');
  background-size: cover;
  transform: rotate(-2deg);

  img {
    width: 95%;
    transform: rotate(2deg);
  }

  .face {
    z-index: -1;
    position: absolute;
    top: -70px;
    right: 120px;
    width: 25%;
    transform: rotate(-2deg);
  }
}
</style>
