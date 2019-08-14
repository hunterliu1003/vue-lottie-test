<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />
    <div style="display: flex; justify-content: center;">
      <div>
        borderCount {{ borderCount }}
        <button @click="setBorder">border version</button>
        <BetChipBorder v-for="i in borderCount" :key="i" />
      </div>
      <div style="width: 50px;"></div>
      <div>
        ellipseCount {{ ellipseCount }}
        <button @click="setEllipse">ellipse version</button>
        <BetChipEllipse v-for="i in ellipseCount" :key="i" />
      </div>
      <div style="width: 50px;"></div>
      <div>
        svgCount {{ svgCount }}
        <button @click="setSVG">svg version</button>
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
    </div>
  </div>
</template>

<script>
import BetChipBorder from "@/components/BetChipBorder.vue";
import BetChipEllipse from "@/components/BetChipEllipse.vue";
import BetChipSVG from "@/components/BetChipSVG.vue";
import { setInterval, clearInterval } from "timers";

export default {
  name: "home",
  components: {
    BetChipBorder,
    BetChipEllipse,
    BetChipSVG
  },
  data: () => ({
    borderCount: 0,
    ellipseCount: 0,
    svgCount: 0,
    borderInterval: 0,
    ellipseInterval: 0,
    svgInterval: 0
  }),
  // mounted() {
  //   this.intervalId = setInterval(() => {
  //     this.borderCount += 1;
  //   }, 40);
  // },
  methods: {
    reset() {
      clearInterval(this.borderInterval);
      clearInterval(this.ellipseInterval);
      clearInterval(this.svgInterval);
      this.borderCount = 0;
      this.ellipseCount = 0;
      this.svgCount = 0;
    },
    setBorder() {
      this.reset();
      this.borderInterval = setInterval(() => {
        if (this.borderCount === 500) {
          clearInterval(this.borderInterval);
        } else {
          this.borderCount += 1;
        }
      }, 40);
    },
    setEllipse() {
      this.reset();
      this.ellipseInterval = setInterval(() => {
        if (this.ellipseCount === 500) {
          clearInterval(this.ellipseInterval);
        } else {
          this.ellipseCount += 1;
        }
      }, 40);
    },
    setSVG() {
      this.reset();
      this.svgInterval = setInterval(() => {
        if (this.svgCount === 500) {
          clearInterval(this.svgInterval);
        } else {
          this.svgCount += 1;
        }
      }, 40);
    }
  }
};
</script>
