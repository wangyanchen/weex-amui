<template>
  <slider
    :auto-play="true"
    :style="{flex: 1}"
    :infinite="true"
    :index="index"
    :scrollable="canScroll"
    @change="handelChange"
  >
    <slot></slot>
  </slider>
</template>

<script>

export default {
  name: 'am-native-tab-container',
  props: {
    index: {
      type: Number,
      default: 1
    },
    width: {
      type: [Number, String],
      default: 750
    },
    canScroll: {
      type: Boolean,
      default: false
    }
  },
  methods: {
    handelChange ($event) {
      this.$emit('update:index', $event.index)
      this.$emit('change', $event.index)
    }
  },
  watch: {
    index (val) {
      if (val !== this.index) {
        this.$emit('update:index', val)
      }
    }
  }
}
</script>
