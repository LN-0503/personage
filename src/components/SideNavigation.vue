<template>
  <div class="side-nav">
    <div class="nav-line"></div>
    <div 
      v-for="(section, index) in sections" 
      :key="section.id"
      class="nav-dot-container"
    >
      <div 
        class="nav-dot"
        :class="{ active: currentSection === section.id }"
        @click="$emit('navigate', section.id)"
        @mouseenter="hoveredSection = section.id"
        @mouseleave="hoveredSection = null"
      >
        <span class="tooltip">{{ section.name }}</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'SideNavigation',
  props: {
    sections: {
      type: Array,
      required: true
    },
    currentSection: {
      type: String,
      default: 'home'
    }
  },
  data() {
    return {
      hoveredSection: null
    }
  }
}
</script>

<style scoped>
.side-nav {
  position: fixed;
  right: 32px;
  top: 50%;
  transform: translateY(-50%);
  z-index: 999;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0;
}

.nav-line {
  position: absolute;
  width: 2px;
  height: 100%;
  background: linear-gradient(
    to bottom,
    transparent,
    rgba(255, 255, 255, 0.2) 20%,
    rgba(255, 255, 255, 0.2) 80%,
    transparent
  );
  border-radius: 1px;
}

.nav-dot-container {
  position: relative;
  z-index: 1;
}

.nav-dot {
  width: 12px;
  height: 12px;
  border-radius: 50%;
  background: rgba(255, 255, 255, 0.3);
  border: 2px solid rgba(255, 255, 255, 0.5);
  cursor: pointer;
  transition: all 0.3s ease;
  position: relative;
  margin: 16px 0;
}

.nav-dot:hover {
  background: rgba(255, 255, 255, 0.6);
  transform: scale(1.3);
}

.nav-dot.active {
  background: var(--accent-cyan);
  border-color: var(--accent-cyan);
  box-shadow: 0 0 15px var(--accent-cyan);
  transform: scale(1.4);
}

.tooltip {
  position: absolute;
  right: 24px;
  top: 50%;
  transform: translateY(-50%);
  background: rgba(0, 0, 0, 0.8);
  color: white;
  padding: 6px 12px;
  border-radius: 6px;
  font-size: 12px;
  white-space: nowrap;
  opacity: 0;
  pointer-events: none;
  transition: opacity 0.2s ease;
  backdrop-filter: blur(10px);
  border: 1px solid rgba(255, 255, 255, 0.1);
}

.tooltip::after {
  content: '';
  position: absolute;
  right: -6px;
  top: 50%;
  transform: translateY(-50%);
  border: 6px solid transparent;
  border-left-color: rgba(0, 0, 0, 0.8);
}

.nav-dot:hover .tooltip {
  opacity: 1;
}

@media (max-width: 768px) {
  .side-nav {
    display: none;
  }
}
</style>
