<template>
  <div
    class="
      flex flex-col
      justify-center
      items-center
      min-h-screen
      bg-gray-400
      relative
    "
  >
    <canvas ref="canvas" width="600" height="600" class="bg-white"></canvas>
  </div>
</template>

<script>
export default {
  data() {
    return {
      ctx: null,
      circle: { x: 200, y: 200, size: 30, dx: 5, dy: 4 },
    }
  },
  computed: {},
  watch: {},
  mounted() {},
}
</script>

<style></style>
