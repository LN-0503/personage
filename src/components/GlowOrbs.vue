<template>
  <div class="glow-orbs">
    <div class="orb orb-1"></div>
    <div class="orb orb-2"></div>
    <div class="orb orb-3"></div>
  </div>
</template>

<script>
export default {
  name: 'GlowOrbs'
}
</script>

<style scoped>
.glow-orbs {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: 0;
  pointer-events: none;
  overflow: hidden;
}

.orb {
  position: absolute;
  border-radius: 50%;
  filter: blur(100px);
  opacity: 0.4;
}

.orb-1 {
  width: 600px;
  height: 600px;
  background: radial-gradient(circle, var(--accent-cyan) 0%, transparent 70%);
  top: -200px;
  right: -100px;
  animation: drift-1 12s ease-in-out infinite;
}

.orb-2 {
  width: 500px;
  height: 500px;
  background: radial-gradient(circle, var(--accent-purple) 0%, transparent 70%);
  bottom: -150px;
  left: -100px;
  animation: drift-2 15s ease-in-out infinite;
}

.orb-3 {
  width: 400px;
  height: 400px;
  background: radial-gradient(circle, var(--accent-pink) 0%, transparent 70%);
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  animation: drift-3 10s ease-in-out infinite;
}

@keyframes drift-1 {
  0%, 100% {
    transform: translate(0, 0) scale(1);
    opacity: 0.4;
  }
  33% {
    transform: translate(-50px, 50px) scale(1.1);
    opacity: 0.5;
  }
  66% {
    transform: translate(30px, -30px) scale(0.95);
    opacity: 0.35;
  }
}

@keyframes drift-2 {
  0%, 100% {
    transform: translate(0, 0) scale(1);
    opacity: 0.35;
  }
  50% {
    transform: translate(80px, -60px) scale(1.15);
    opacity: 0.5;
  }
}

@keyframes drift-3 {
  0%, 100% {
    transform: translate(-50%, -50%) scale(1);
    opacity: 0.3;
  }
  25% {
    transform: translate(-45%, -55%) scale(1.1);
    opacity: 0.4;
  }
  75% {
    transform: translate(-55%, -45%) scale(0.9);
    opacity: 0.25;
  }
}
</style>
