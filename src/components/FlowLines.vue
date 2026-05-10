<template>
  <svg class="flow-lines" xmlns="http://www.w3.org/2000/svg">
    <defs>
      <linearGradient id="line-gradient-1" x1="0%" y1="0%" x2="100%" y2="0%">
        <stop offset="0%" stop-color="#00d4ff" stop-opacity="0" />
        <stop offset="30%" stop-color="#00d4ff" stop-opacity="0.6" />
        <stop offset="70%" stop-color="#a855f7" stop-opacity="0.6" />
        <stop offset="100%" stop-color="#a855f7" stop-opacity="0" />
      </linearGradient>
      <linearGradient id="line-gradient-2" x1="0%" y1="0%" x2="100%" y2="0%">
        <stop offset="0%" stop-color="#a855f7" stop-opacity="0" />
        <stop offset="30%" stop-color="#a855f7" stop-opacity="0.5" />
        <stop offset="70%" stop-color="#ec4899" stop-opacity="0.5" />
        <stop offset="100%" stop-color="#ec4899" stop-opacity="0" />
      </linearGradient>
      <linearGradient id="line-gradient-3" x1="0%" y1="0%" x2="100%" y2="0%">
        <stop offset="0%" stop-color="#ec4899" stop-opacity="0" />
        <stop offset="50%" stop-color="#00d4ff" stop-opacity="0.4" />
        <stop offset="100%" stop-color="#00d4ff" stop-opacity="0" />
      </linearGradient>
    </defs>
    
    <path class="flow-path" d="M-100,200 Q300,100 600,300 T1200,200 T1800,300" />
    <path class="flow-path" d="M-100,500 Q400,400 700,550 T1400,450 T2000,550" />
    <path class="flow-path" d="M-100,800 Q350,700 650,850 T1300,750 T1900,850" />
    <path class="flow-path reverse" d="M2000,150 Q1600,250 1200,100 T400,200 T-200,100" />
    <path class="flow-path reverse" d="M2000,600 Q1500,500 1000,650 T200,550 T-400,650" />
    <path class="flow-path reverse" d="M2000,900 Q1400,800 800,950 T0,850 T-600,950" />
  </svg>
</template>

<script>
export default {
  name: 'FlowLines'
}
</script>

<style scoped>
.flow-lines {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: 1;
  pointer-events: none;
  overflow: visible;
}

.flow-path {
  fill: none;
  stroke-width: 2;
  stroke-linecap: round;
  stroke-dasharray: 300 600;
  animation: flow 12s linear infinite;
}

.flow-path:nth-child(1) { stroke: url(#line-gradient-1); animation-duration: 14s; }
.flow-path:nth-child(2) { stroke: url(#line-gradient-2); animation-duration: 11s; }
.flow-path:nth-child(3) { stroke: url(#line-gradient-1); animation-duration: 16s; }
.flow-path:nth-child(4) { stroke: url(#line-gradient-3); animation-duration: 13s; }
.flow-path:nth-child(5) { stroke: url(#line-gradient-2); animation-duration: 15s; }
.flow-path:nth-child(6) { stroke: url(#line-gradient-3); animation-duration: 12s; }

.flow-path.reverse {
  animation-direction: reverse;
}

@keyframes flow {
  0% {
    stroke-dashoffset: 900;
  }
  100% {
    stroke-dashoffset: 0;
  }
}
</style>
