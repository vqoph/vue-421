<template>
  <div class="dice">
    <div class="dice-value">{{ value }}</div>
    <button
      @click="$emit('change', value)"
      :style="{ display: keeped ? 'none' : 'initial' }"
    >
      garder
    </button>
  </div>
</template>

<script>
export default {
  props: {
    value: { type: Number },
    keeped: { type: Boolean, default: false },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.dice {
}
</style>
