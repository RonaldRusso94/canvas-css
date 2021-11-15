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
    }
  },
  mounted() {
    this.ctx = this.$refs.canvas.getContext('2d')
    const ctx = this.ctx

    // TRIANGLE
    ctx.beginPath()
    ctx.moveTo(50, 50)
    ctx.lineTo(150, 50)
    ctx.lineTo(100, 200)
    ctx.lineTo(50, 50)
    // ctx.closePath()
    // ctx.stroke()
    ctx.fillStyle = 'coral'
    ctx.fill()

    // TRIANGLE
    ctx.beginPath()
    ctx.moveTo(200, 50)
    ctx.lineTo(150, 200)
    ctx.lineTo(250, 200)
    ctx.closePath()
    ctx.stroke()

    // RECTANGLE
    ctx.beginPath()
    ctx.rect(300, 50, 150, 100)
    ctx.fillStyle = 'teal'
    ctx.fill()

    // DRAW HEAD
    ctx.beginPath()
    const centerX = this.$refs.canvas.width / 2
    const centerY = this.$refs.canvas.height / 1.5
    ctx.arc(centerX, centerY, 100, 0, Math.PI * 2)

    // Move to mouth
    ctx.moveTo(centerX + 60, centerY)

    // Draw mouth
    ctx.arc(centerX, centerY, 60, 0, Math.PI, false)

    // Move To Left Eye
    ctx.moveTo(centerX - 25, centerY - 40)

    // Draw Left Eye
    ctx.arc(centerX - 40, centerY - 40, 15, 0, Math.PI * 2)

    // Move to right eye
    ctx.moveTo(centerX + 55, centerY - 40)

    // Draw Right Eye
    ctx.arc(centerX + 40, centerY - 40, 15, 0, Math.PI * 2)

    ctx.stroke()
  },
}
</script>

<style></style>
