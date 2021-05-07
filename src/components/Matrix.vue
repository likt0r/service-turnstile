<template>
  <canvas class="canvas" ref="canvas"></canvas>
</template>

<script>
const str =
  "'A+jk js:2 @dfs 17 tr YY ufds M5r Ä# P87 #18 $!& ^dfs $Ew er JH # $ * . (! ;) ,: : ご 購 入 は フ ォン ト の 部 分 を クリ ック し て 買い物 か ご に 入& れ る だ% け '"
export default {
  data() {
    return {
      ctx: null,
      font: 16,
      width: 0,
      height: 0,
      col: 0,

      matrix: str.split(' '),
      arr: [],
    }
  },
  methods: {
    shuffleArray(arr) {
      for (let i = arr.length - 1; i > 0; i--) {
        const j = Math.floor(Math.random() * (i + 1))
        ;[arr[i], arr[j]] = [arr[j], arr[i]]
      }
    },
    draw() {
      this.ctx.fillStyle = 'rgba(0,0,0,0.02)'
      this.ctx.fillRect(0, 0, this.width, this.height)
      this.ctx.fillStyle = '#00FF00'
      this.ctx.font = `${this.font}px system-ui`
      this.shuffleArray(this.matrix)
      for (let i = 0; i < this.arr.length; i++) {
        let txt = this.matrix[Math.floor(Math.random() * this.matrix.length)]
        this.ctx.fillText(txt, i * this.font, this.arr[i] * this.font)
        if (this.arr[i] * this.font > this.height && Math.random() > 0.985) {
          this.arr[i] = 0
        }
        this.arr[i]++
      }
    },
  },
  mounted() {
    const canvas = this.$refs.canvas
    console.log(this.$refs.canvas)
    this.ctx = canvas.getContext('2d')
    this.width = canvas.width = window.innerWidth
    this.height = canvas.height = window.innerHeight
    this.col = this.width / this.font

    for (let i = 0; i < this.col; i++) {
      this.arr[i] = 1
    }

    setInterval(this.draw, 35)
    window.addEventListener('resize', () => location.reload())
  },
}
</script>
<style scoped>
.canvas {
  position: fixed;
  top: 0;
  left: 0;
}
</style>
