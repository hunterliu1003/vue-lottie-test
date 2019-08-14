<template functional>
  <svg
    :width="props.width"
    :height="props.height"
    version="1.1"
    xmlns="http://www.w3.org/2000/svg"
    xmlns:xlink="http://www.w3.org/1999/xlink"
  >
    <!-- <g> -->
    <mask :id="`ellipseOuterMask${props.maskId}`">
      <rect
        :x="-props.padding"
        :y="
          props.offsetY + props.height / 2 - (props.height / 2 + props.padding)
        "
        :width="props.width + props.padding * 2"
        :height="props.height + props.padding * 2"
        fill="#fff"
      />
      <ellipse
        class="ellipse-outer-mask"
        :cx="props.width / 2"
        :cy="props.offsetY + props.height / 2"
        :rx="props.width / 2 + props.padding"
        :ry="props.height / 2 + props.padding"
        fill="#000"
      />
    </mask>
    <ellipse
      class="ellipse-outer"
      :cx="props.width / 2"
      :cy="props.offsetY + props.height / 2"
      :rx="props.width / 2 + props.padding"
      :ry="props.height / 2 + props.padding"
      fill="#D3B27A"
      :mask="`url(#ellipseOuterMask${props.maskId})`"
    />

    <mask :id="`ellipseInnerMask${props.maskId}`">
      <rect
        :x="-props.padding"
        :y="
          props.offsetY + props.height / 2 - (props.height / 2 + props.padding)
        "
        :width="props.width + props.padding * 2"
        :height="props.height + props.padding * 2"
        fill="#fff"
      />
      <ellipse
        class="ellipse-inner-mask"
        :cx="props.width / 2"
        :cy="props.offsetY + props.height / 2"
        :rx="props.width / 2 + props.padding"
        :ry="props.height / 2 + props.padding"
        fill="#000"
      />
    </mask>
    <ellipse
      class="ellipse-inner"
      :cx="props.width / 2"
      :cy="props.offsetY + props.height / 2"
      :rx="props.width / 2 + props.padding"
      :ry="props.height / 2 + props.padding"
      fill="#FFEBC7"
      :mask="`url(#ellipseInnerMask${props.maskId})`"
    />
    <!-- </g> -->
  </svg>
</template>

<script>
export default {
  props: {
    width: {
      required: true
    },
    height: {
      required: true
    },
    padding: {
      required: true
    },
    offsetY: {
      required: true
    },
    maskId: {
      required: true
    }
  }
};
</script>

<style lang="scss" scoped>
.ellipse-outer {
  transform-box: fill-box;
  animation: scale-outer 6s linear infinite;
  transform-origin: 50% 50%;
  transform: scale(0.35);
}
.ellipse-outer-mask {
  transform-box: fill-box;
  animation: scale-outer-mask 6s linear infinite;
  transform-origin: 50% 50%;
  transform: scale(0.35);
  will-change: transform, opacity;
}
@keyframes scale-outer {
  0% {
    transform: scale(0.35);
    opacity: 1;
  }
  8% {
    transform: scale(1);
    opacity: 0;
  }
  99% {
    transform: scale(1);
    opacity: 0;
  }
  100% {
    transform: scale(1);
    opacity: 0;
  }
}
@keyframes scale-outer-mask {
  0% {
    transform: scale(0.35);
  }
  8% {
    transform: scale(1);
  }
  99% {
    transform: scale(1);
  }
  100% {
    transform: scale(1);
  }
}
.ellipse-inner {
  transform-box: fill-box;
  animation: scale-inner 6s linear infinite;
  transform-origin: 50% 50%;
  transform: scale(0.35);
  will-change: transform, opacity;
}
.ellipse-inner-mask {
  transform-box: fill-box;
  animation: scale-inner-mask 6s linear infinite;
  transform-origin: 50% 50%;
  transform: scale(0.35);
}
@keyframes scale-inner {
  0% {
    transform: scale(0.35);
    opacity: 1;
  }
  4% {
    transform: scale(0.35);
    opacity: 1;
  }
  12% {
    transform: scale(1);
    opacity: 0;
  }
  99% {
    transform: scale(1);
    opacity: 0;
  }
  100% {
    transform: scale(1);
    opacity: 0;
  }
}
@keyframes scale-inner-mask {
  0% {
    transform: scale(0.35);
  }
  4% {
    transform: scale(0.35);
  }
  12% {
    transform: scale(1);
  }
  99% {
    transform: scale(1);
  }
  100% {
    transform: scale(1);
  }
}
</style>
