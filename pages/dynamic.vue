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
    <canvas
      ref="canvas"
      width="600"
      height="600"
      class="bg-white shadow-lg rounded"
    ></canvas>

    <div class="flex items-center justify-center h-12 w-full space-x-8 mt-2">
      <button
        class="bg-gray-200 rounded px-4 py-1 font-bold shadow-lg"
        @click="drawRect"
      >
        Add Rectangle
      </button>

      <div class="flex space-x-2">
        <button class="bg-gray-200 rounded px-4 py-1 font-bold shadow-lg w-12">
          -
        </button>
        <button class="bg-gray-200 rounded px-4 py-1 font-bold shadow-lg w-12">
          +
        </button>
      </div>
    </div>
  </div>
</template>

<script>
// import '../components/canvasScript.js'
export default {
  data() {
    return {
      ctx: null,
      rectWidth: 100,
      rectHeight: 100,
      zoom: false,
    }
  },
  mounted() {
    this.ctx = this.$refs.canvas.getContext('2d')
  },
  methods: {
    drawRect() {
      // Clear Canvas
      this.ctx.clearRect(
        0,
        0,
        // this.$refs.canvas.width,
        // this.$refs.canvas.height
        600,
        600
      )

      // Draw Rect
      // draw rect
      this.ctx.beginPath()
      this.ctx.rect(20, 20, this.rectWidth, this.rectHeight)
      this.ctx.stroke()
    },
    addWidth() {
      this.rectWidth += 10
      this.drawRect()
    },
    subWidth() {
      this.rectWidth -= 10
      this.drawRect()
    },
  },
}
</script>
