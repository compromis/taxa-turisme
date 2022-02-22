<template>
    <div class="bob-title">
      <img src="@/assets/images/spongebob/title-bob.svg" alt="Però això farà que el turisme baixe!">
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
  border-radius: clamp(2rem, 2vw, 4rem);
  padding: clamp(3rem, 5vw, 6rem) clamp(1.5rem, 2vw, 3rem);
  background-image: url('../assets/images/spongebob/background.webp');
  background-size: cover;
  transform: rotate(-2deg);

  img {
    transform: rotate(2deg);
    width: 100%;
  }

  .face {
    z-index: -1;
    position: absolute;
    top: -18%;
    right: 10%;
    width: 25%;
    transform: rotate(-2deg);
  }
}
</style>
