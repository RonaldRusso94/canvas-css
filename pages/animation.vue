<template>
  <div
    class="flex flex-col justify-center items-center min-h-screen bg-gray-400"
  >
    <canvas
      ref="canvas"
      width="600"
      height="600"
      class="bg-white shadow-lg rounded"
    ></canvas>

    <div class="w-[600px] mt-4 flex justify-around">
      <div class="flex">
        <h2 class="font-bold text-xl mr-2">Speed:</h2>
        <div class="space-x-1">
          <button
            class="bg-gray-200 h-8 rounded px-4 font-bold"
            @click="subSpeed"
          >
            -
          </button>
          <button
            class="bg-gray-200 h-8 rounded px-4 font-bold"
            @click="addSpeed"
          >
            +
          </button>
        </div>
      </div>
      <button class="bg-gray-200 h-8 rounded px-4 font-bold" @click="stopBall">
        Stop
      </button>
      <div class="flex">
        <h2 class="font-bold text-xl mr-2">Gravity:</h2>
        <div class="space-x-1">
          <button
            class="bg-gray-200 h-8 rounded px-4 font-bold"
            @click="subGravity"
          >
            -
          </button>
          <button
            class="bg-gray-200 h-8 rounded px-4 font-bold"
            @click="addGravity"
          >
            +
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      ctx: null,
      circle: { x: 200, y: 200, size: 30, dx: 1, dy: 1 },
    }
  },
  computed: {},
  watch: {},
  mounted() {
    this.ctx = this.$refs.canvas.getContext('2d')
    // const ctx = this.ctx
    // Animation 1

    this.drawCircle()
    this.update()
  },
  methods: {
    drawCircle() {
      this.ctx.beginPath()
      this.ctx.arc(
        this.circle.x,
        this.circle.y,
        this.circle.size,
        0,
        Math.PI * 2
      )
      this.ctx.filStyle = 'purple'
      this.ctx.fill()
    },
    update() {
      this.ctx.clearRect(
        0,
        0,
        this.$refs.canvas.width,
        this.$refs.canvas.height
      )
      this.drawCircle()

      // change position
      this.circle.x += this.circle.dx
      this.circle.y += this.circle.dy

      // Detect Side Walls
      if (
        this.circle.x + this.circle.size > this.$refs.canvas.width ||
        this.circle.x - this.circle.size < 0
      ) {
        this.circle.dx *= -1
      }

      // Detect Top & Bottom walls
      if (
        this.circle.y + this.circle.size > this.$refs.canvas.height ||
        this.circle.y - this.circle.size < 0
      ) {
        this.circle.dy *= -1
      }

      requestAnimationFrame(this.update)
    },
    addSpeed() {
      if (this.circle.dx > 0) {
        this.circle.dx += 0.5
      } else if (this.circle.dx < 0) {
        this.circle.dx -= 0.5
      } else if (this.circle.dx === 0) {
        this.circle.dx += 0.5
      }
    },
    subSpeed() {
      if (this.circle.dx > 0) {
        this.circle.dx -= 0.5
      } else if (this.circle.dx < 0) {
        this.circle.dx += 0.5
      }
    },
    addGravity() {
      if (this.circle.dy >= 0) {
        this.circle.dy += 0.5
      } else if (this.circle.dy < 0) {
        this.circle.dy -= 0.5
      }
    },
    subGravity() {
      if (this.circle.dy > 0) {
        this.circle.dy -= 0.5
      } else if (this.circle.dy < 0) {
        this.circle.dy += 0.5
      }
    },
    stopBall() {
      this.circle.dx = 0
      this.circle.dy = 0
    },
  },
}
</script>

<style></style>
