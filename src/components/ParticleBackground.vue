<template>
  <canvas ref="canvas" class="particle-canvas"></canvas>
</template>

<script>
export default {
  name: 'ParticleBackground',
  mounted() {
    this.canvas = this.$refs.canvas
    this.ctx = this.canvas.getContext('2d')
    this.particles = []
    this.mouseX = 0
    this.mouseY = 0
    
    this.resize()
    this.createParticles()
    this.animate()
    
    window.addEventListener('resize', () => this.resize())
    window.addEventListener('mousemove', (e) => {
      this.mouseX = e.clientX
      this.mouseY = e.clientY
    })
  },
  beforeDestroy() {
    window.removeEventListener('resize', () => this.resize())
  },
  methods: {
    resize() {
      this.canvas.width = window.innerWidth
      this.canvas.height = window.innerHeight
    },
    createParticles() {
      const particleCount = Math.min(150, Math.floor((window.innerWidth * window.innerHeight) / 15000))
      this.particles = []
      
      for (let i = 0; i < particleCount; i++) {
        const hue = Math.random() > 0.8 ? (Math.random() > 0.5 ? 190 : 270) : 0
        this.particles.push({
          x: Math.random() * this.canvas.width,
          y: Math.random() * this.canvas.height,
          size: Math.random() * 2 + 1,
          speedX: (Math.random() - 0.5) * 0.3,
          speedY: (Math.random() - 0.5) * 0.3,
          opacity: Math.random() * 0.5 + 0.3,
          hue: hue,
          saturation: hue === 0 ? 0 : 100,
          lightness: hue === 0 ? 100 : 70
        })
      }
    },
    animate() {
      this.ctx.clearRect(0, 0, this.canvas.width, this.canvas.height)
      
      const centerX = this.canvas.width / 2
      const centerY = this.canvas.height / 2
      
      this.particles.forEach(particle => {
        const dx = this.mouseX - centerX
        const dy = this.mouseY - centerY
        const dist = Math.sqrt(dx * dx + dy * dy)
        const maxDist = Math.min(this.canvas.width, this.canvas.height) / 2
        
        if (dist < maxDist) {
          const force = (maxDist - dist) / maxDist * 0.02
          particle.x += dx * force * 0.1
          particle.y += dy * force * 0.1
        }
        
        particle.x += particle.speedX
        particle.y += particle.speedY
        
        if (particle.x < 0) particle.x = this.canvas.width
        if (particle.x > this.canvas.width) particle.x = 0
        if (particle.y < 0) particle.y = this.canvas.height
        if (particle.y > this.canvas.height) particle.y = 0
        
        this.ctx.beginPath()
        this.ctx.arc(particle.x, particle.y, particle.size, 0, Math.PI * 2)
        this.ctx.fillStyle = `hsla(${particle.hue}, ${particle.saturation}%, ${particle.lightness}%, ${particle.opacity})`
        this.ctx.fill()
      })
      
      this.drawConnections()
      requestAnimationFrame(() => this.animate())
    },
    drawConnections() {
      for (let i = 0; i < this.particles.length; i++) {
        for (let j = i + 1; j < this.particles.length; j++) {
          const dx = this.particles[i].x - this.particles[j].x
          const dy = this.particles[i].y - this.particles[j].y
          const distance = Math.sqrt(dx * dx + dy * dy)
          
          if (distance < 120) {
            const opacity = (1 - distance / 120) * 0.15
            const gradient = this.ctx.createLinearGradient(
              this.particles[i].x, this.particles[i].y,
              this.particles[j].x, this.particles[j].y
            )
            gradient.addColorStop(0, `rgba(0, 212, 255, ${opacity})`)
            gradient.addColorStop(1, `rgba(168, 85, 247, ${opacity})`)
            
            this.ctx.beginPath()
            this.ctx.moveTo(this.particles[i].x, this.particles[i].y)
            this.ctx.lineTo(this.particles[j].x, this.particles[j].y)
            this.ctx.strokeStyle = gradient
            this.ctx.lineWidth = 0.5
            this.ctx.stroke()
          }
        }
      }
    }
  }
}
</script>

<style scoped>
.particle-canvas {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: 0;
  pointer-events: none;
}
</style>
