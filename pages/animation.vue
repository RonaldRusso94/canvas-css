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

      requestAnimationFrame(this.update)
      // console.log(123)
    },
  },
}
</script>

<style></style>
