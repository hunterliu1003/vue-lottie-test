<template>
  <div class="hello">
    <div class="lottie-border" ref="betChip"></div>
  </div>
</template>

<script>
import lottie from "lottie-web";
export default {
  mounted() {
    let anim = lottie.loadAnimation({
      container: this.$refs["betChip"],
      renderer: "svg",
      loop: false,
      autoplay: true,
      path: "/bet_chip_0812.json"
    });
    anim.addEventListener("complete", function() {
      setTimeout(function() {
        anim.goToAndPlay(0);
      }, 5000);
    });
  }
};
</script>

<style lang="scss" scoped>
.lottie-border {
  display: inline-block;
  width: 80px;
  height: 80px;
  transform: rotateX(60deg);
}
</style>
