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

    <div class="flex w-[600px] mt-2">
      <div class="w-2/4 flex justify-center items-center">
        <button
          class="bg-gray-200 rounded px-4 py-1 font-bold shadow-lg"
          @click="start()"
        >
          {{ canvasStart ? 'Reset Rectangle' : 'Add Rectangle' }}
        </button>
      </div>

      <div class="w-2/4 flex justify-center">
        <div>
          <div class="flex items-center space-x-2">
            <h2 class="font-bold text-xl mr-2">Width:</h2>

            <button
              class="bg-gray-200 rounded px-4 py-1 font-bold shadow-lg w-12"
              @click="subWidth"
            >
              -
            </button>
            <button
              class="bg-gray-200 rounded px-4 py-1 font-bold shadow-lg w-12"
              @click="addWidth"
            >
              +
            </button>
          </div>

          <div class="flex items-center space-x-2 mt-4">
            <h2 class="font-bold text-xl mr-2">Height:</h2>
            <button
              class="bg-gray-200 rounded px-4 py-1 font-bold shadow-lg w-12"
              @click="subHeight"
            >
              -
            </button>
            <button
              class="bg-gray-200 rounded px-4 py-1 font-bold shadow-lg w-12"
              @click="addHeight"
            >
              +
            </button>
          </div>
        </div>
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
      canvasStart: false,
    }
  },
  mounted() {
    this.ctx = this.$refs.canvas.getContext('2d')
  },
  methods: {
    start() {
      this.rectWidth = 100
      this.rectHeight = 100
      this.drawRect()
    },
    drawRect() {
      // Clear Canvas
      this.canvasStart = true
      this.ctx.clearRect(
        0,
        0,
        this.$refs.canvas.width,
        this.$refs.canvas.height
        // 600,
        // 600
      )

      // Draw Rect
      this.ctx.beginPath()
      this.ctx.rect(20, 20, this.rectWidth, this.rectHeight)
      this.ctx.stroke()
    },
    addWidth() {
      if (this.canvasStart) {
        this.rectWidth += 10
        this.drawRect()
      }
    },
    subWidth() {
      if (this.canvasStart) {
        this.rectWidth -= 10
        this.drawRect()
      }
    },
    addHeight() {
      if (this.canvasStart) {
        this.rectHeight += 10
        this.drawRect()
      }
    },
    subHeight() {
      if (this.canvasStart) {
        this.rectHeight -= 10
        this.drawRect()
      }
    },
  },
}
</script>
