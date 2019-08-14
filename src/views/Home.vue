<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />
    <button @click="setAll" style="display: block; margin: 20px auto 10px;">
      all count
    </button>
    <input
      type="text"
      v-model="defaultCount"
      style="display: block; margin: 0 auto 20px;"
    />
    <div style="display: flex; justify-content: center;">
      <div>
        borderCount {{ borderCount }}
        <button @click="start('borderCount')">border version</button>
        <BetChipBorder v-for="i in borderCount" :key="i" />
      </div>
      <div style="width: 50px;"></div>
      <div>
        ellipseCount {{ ellipseCount }}
        <button @click="start('ellipseCount')">ellipse version</button>
        <BetChipEllipse v-for="i in ellipseCount" :key="i" />
      </div>
      <div style="width: 50px;"></div>
      <div>
        svgCount {{ svgCount }}
        <button @click="start('svgCount')">svg version</button>
        <div v-for="i in svgCount" :key="i" style="padding: 15px;">
          <BetChipSVG
            :width="80"
            :height="36"
            :padding="0"
            :maskId="`betChipSVG${i}`"
            :offsetY="0"
          />
        </div>
      </div>
      <div style="width: 50px;"></div>
      <div>
        svgFuncCount {{ svgFuncCount }}
        <button @click="start('svgFuncCount')">svgFunc version</button>
        <div v-for="i in svgFuncCount" :key="i" style="padding: 15px;">
          <BetChipSVGFunc
            :width="80"
            :height="36"
            :padding="0"
            :maskId="`betChipSVGFunc${i}`"
            :offsetY="0"
          />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import BetChipBorder from "@/components/BetChipBorder.vue";
import BetChipEllipse from "@/components/BetChipEllipse.vue";
import BetChipSVG from "@/components/BetChipSVG.vue";
import BetChipSVGFunc from "@/components/BetChipSVGFunc.vue";
import { setInterval, clearInterval } from "timers";

export default {
  name: "home",
  components: {
    BetChipBorder,
    BetChipEllipse,
    BetChipSVG,
    BetChipSVGFunc
  },
  data: () => ({
    borderCount: 0,
    ellipseCount: 0,
    svgCount: 0,
    svgFuncCount: 0,
    allCount: 0,
    allInterval: 0,
    defaultCount: 100
  }),
  methods: {
    setAll() {
      this.allInterval = setInterval(() => {
        if (this.allCount === +this.defaultCount) {
          clearInterval(this.allInterval);
        } else {
          this.allCount += 1;
          this.borderCount = this.allCount;
          this.ellipseCount = this.allCount;
          this.svgCount = this.allCount;
          this.svgFuncCount = this.allCount;
        }
      }, 40);
    },
    start(anim) {
      this.reset();
      this.allInterval = setInterval(() => {
        if (this.allCount === +this.defaultCount) {
          clearInterval(this.allInterval);
        } else {
          this.allCount += 1;
          this[anim] = this.allCount;
        }
      }, 40);
    },
    reset() {
      clearInterval(this.allInterval);
      this.borderCount = 0;
      this.ellipseCount = 0;
      this.svgCount = 0;
      this.svgFuncCount = 0;
      this.allCount = 0;
    }
  }
};
</script>

<style lang="scss" scoped>
.home {
}
</style>
