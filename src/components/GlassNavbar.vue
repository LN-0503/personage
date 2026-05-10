<template>
  <nav class="glass-navbar" :class="{ scrolled: isScrolled }">
    <div class="navbar-content">
      <div class="logo">
        <span class="logo-text">FUTURE</span>
      </div>
      <ul class="nav-links">
        <li 
          v-for="section in sections" 
          :key="section.id"
          class="nav-item"
          :class="{ active: currentSection === section.id }"
          @click="$emit('navigate', section.id)"
        >
          <span class="nav-icon">
            <svg v-if="section.icon === 'home'" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
              <path d="M3 9l9-7 9 7v11a2 2 0 01-2 2H5a2 2 0 01-2-2z"/>
              <polyline points="9,22 9,12 15,12 15,22"/>
            </svg>
            <svg v-else-if="section.icon === 'user'" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
              <path d="M20 21v-2a4 4 0 00-4-4H8a4 4 0 00-4 4v2"/>
              <circle cx="12" cy="7" r="4"/>
            </svg>
            <svg v-else-if="section.icon === 'code'" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
              <polyline points="16,18 22,12 16,6"/>
              <polyline points="8,6 2,12 8,18"/>
            </svg>
            <svg v-else-if="section.icon === 'folder'" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
              <path d="M22 19a2 2 0 01-2 2H4a2 2 0 01-2-2V5a2 2 0 012-2h5l2 3h9a2 2 0 012 2z"/>
            </svg>
            <svg v-else-if="section.icon === 'mail'" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
              <path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"/>
              <polyline points="22,6 12,13 2,6"/>
            </svg>
          </span>
          <span class="nav-text">{{ section.name }}</span>
        </li>
      </ul>
    </div>
  </nav>
</template>

<script>
export default {
  name: 'GlassNavbar',
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
      isScrolled: false
    }
  },
  mounted() {
    window.addEventListener('scroll', this.handleScroll)
  },
  beforeDestroy() {
    window.removeEventListener('scroll', this.handleScroll)
  },
  methods: {
    handleScroll() {
      this.isScrolled = window.scrollY > 50
    }
  }
}
</script>

<style scoped>
.glass-navbar {
  position: fixed;
  top: 24px;
  left: 50%;
  transform: translateX(-50%);
  z-index: 1000;
  background: rgba(255, 255, 255, 0.05);
  backdrop-filter: blur(20px);
  -webkit-backdrop-filter: blur(20px);
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 20px;
  padding: 12px 32px;
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  animation: slide-down 0.8s ease-out;
}

.glass-navbar.scrolled {
  background: rgba(255, 255, 255, 0.08);
  box-shadow: 0 8px 32px rgba(0, 212, 255, 0.1);
}

.navbar-content {
  display: flex;
  align-items: center;
  gap: 48px;
}

.logo {
  display: flex;
  align-items: center;
}

.logo-text {
  font-family: 'Orbitron', monospace;
  font-size: 18px;
  font-weight: 700;
  letter-spacing: 0.15em;
  background: linear-gradient(135deg, #00d4ff, #a855f7);
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
  text-shadow: 0 0 20px rgba(0, 212, 255, 0.5);
}

.nav-links {
  display: flex;
  list-style: none;
  gap: 8px;
}

.nav-item {
  display: flex;
  align-items: center;
  gap: 8px;
  padding: 10px 16px;
  border-radius: 12px;
  cursor: pointer;
  transition: all 0.3s ease;
  opacity: 0.8;
  color: var(--text-secondary);
  position: relative;
}

.nav-item:hover {
  opacity: 1;
  background: rgba(255, 255, 255, 0.05);
  color: var(--text-primary);
}

.nav-item.active {
  opacity: 1;
  color: var(--accent-cyan);
}

.nav-item.active::after {
  content: '';
  position: absolute;
  bottom: 4px;
  left: 50%;
  transform: translateX(-50%);
  width: 20px;
  height: 2px;
  background: var(--accent-cyan);
  border-radius: 1px;
  box-shadow: 0 0 10px var(--accent-cyan);
}

.nav-icon {
  width: 18px;
  height: 18px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.nav-icon svg {
  width: 100%;
  height: 100%;
}

.nav-text {
  font-size: 14px;
  font-weight: 500;
  letter-spacing: 0.02em;
}

@keyframes slide-down {
  from {
    opacity: 0;
    transform: translateX(-50%) translateY(-20px);
  }
  to {
    opacity: 1;
    transform: translateX(-50%) translateY(0);
  }
}

@media (max-width: 768px) {
  .glass-navbar {
    bottom: 24px;
    top: auto;
    left: 24px;
    right: 24px;
    transform: none;
    padding: 8px 16px;
  }

  .navbar-content {
    justify-content: space-between;
    gap: 0;
  }

  .nav-text {
    display: none;
  }

  .nav-item {
    padding: 10px;
  }

  .logo {
    display: none;
  }
}
</style>
