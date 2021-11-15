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
// import '../components/canvasScript.js'
export default {
  data() {
    return {
      ctx: null,
    }
  },
  mounted() {
    this.ctx = this.$refs.canvas.getContext('2d')
    // canvas.width = 400
    // console.log(`canvas.width`, canvas.width)

    // fillRect()
    this.ctx.fillStyle = 'red'
    this.ctx.fillRect(20, 20, 150, 100)
    this.ctx.fillStyle = 'blue'
    this.ctx.fillRect(200, 20, 150, 100)

    // strokeRect()
    this.ctx.lineWidth = 5
    this.ctx.strokeStyle = 'green'
    this.ctx.strokeRect(100, 200, 150, 100)

    // clearRect()
    this.ctx.clearRect(25, 25, 140, 90)

    // fillText()
    this.ctx.font = '30px Arial'
    this.ctx.fillStyle = 'purple'
    this.ctx.fillText('Hello World!', 400, 50)

    // strokeText()
    this.ctx.lineWidth = 1
    this.ctx.strokeStyle = 'orange'
    this.ctx.strokeText('Hello World!', 400, 100)
  },
  // computed: {
  //   canvas() {
  //     return true
  //   },
  // },
}
</script>
