<template>
  <section id="home" class="hero-section">
    <div class="hero-content">
      <div class="profile-card glass-card">
        <div class="avatar-container">
          <div class="avatar-ring"></div>
          <div class="avatar-ring-2"></div>
          <img :src="profile.avatar" :alt="profile.name" class="avatar" />
          <div class="avatar-glow"></div>
        </div>
        
        <h1 class="name text-gradient text-glow">{{ profile.name }}</h1>
        <p class="title">{{ profile.title }}</p>
        <p class="subtitle">{{ profile.subtitle }}</p>
        
        <div class="social-links">
          <a 
            v-for="social in profile.socials" 
            :key="social.platform"
            :href="social.url"
            class="social-link"
            target="_blank"
            rel="noopener noreferrer"
          >
            <svg v-if="social.icon === 'github'" viewBox="0 0 24 24" fill="currentColor">
              <path d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/>
            </svg>
            <svg v-else-if="social.icon === 'twitter'" viewBox="0 0 24 24" fill="currentColor">
              <path d="M18.244 2.25h3.308l-7.227 8.26 8.502 11.24H16.17l-5.214-6.817L4.99 21.75H1.68l7.73-8.835L1.254 2.25H8.08l4.713 6.231zm-1.161 17.52h1.833L7.084 4.126H5.117z"/>
            </svg>
            <svg v-else-if="social.icon === 'linkedin'" viewBox="0 0 24 24" fill="currentColor">
              <path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433c-1.144 0-2.063-.926-2.063-2.065 0-1.138.92-2.063 2.063-2.063 1.14 0 2.064.925 2.064 2.063 0 1.139-.925 2.065-2.064 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/>
            </svg>
            <svg v-else-if="social.icon === 'mail'" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"/>
              <polyline points="22,6 12,13 2,6"/>
            </svg>
          </a>
        </div>
        
        <div class="scroll-indicator">
          <span class="scroll-text">向下滚动</span>
          <div class="scroll-arrow">
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <path d="M12 5v14M19 12l-7 7-7-7"/>
            </svg>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'HeroSection',
  props: {
    profile: {
      type: Object,
      required: true
    }
  }
}
</script>

<style scoped>
.hero-section {
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
}

.hero-content {
  position: relative;
  z-index: 10;
}

.profile-card {
  padding: 48px;
  text-align: center;
  max-width: 420px;
  animation: float 6s ease-in-out infinite;
  position: relative;
}

.avatar-container {
  position: relative;
  width: 140px;
  height: 140px;
  margin: 0 auto 32px;
}

.avatar-ring {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  border-radius: 50%;
  background: conic-gradient(from 0deg, #00d4ff, #a855f7, #ec4899, #00d4ff);
  animation: rotate 4s linear infinite;
  padding: 3px;
}

.avatar-ring-2 {
  position: absolute;
  top: 5px;
  left: 5px;
  width: calc(100% - 10px);
  height: calc(100% - 10px);
  border-radius: 50%;
  background: var(--bg-primary);
}

.avatar {
  position: relative;
  width: 100%;
  height: 100%;
  border-radius: 50%;
  object-fit: cover;
  z-index: 1;
}

.avatar-glow {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 160px;
  height: 160px;
  background: radial-gradient(circle, rgba(0, 212, 255, 0.4) 0%, transparent 70%);
  border-radius: 50%;
  animation: pulse-glow 3s ease-in-out infinite;
  z-index: 0;
}

.name {
  font-family: 'Orbitron', monospace;
  font-size: 32px;
  font-weight: 700;
  letter-spacing: 0.1em;
  margin-bottom: 12px;
}

.title {
  font-size: 16px;
  color: var(--text-secondary);
  letter-spacing: 0.2em;
  text-transform: uppercase;
  margin-bottom: 8px;
}

.subtitle {
  font-size: 14px;
  color: var(--text-secondary);
  opacity: 0.7;
  margin-bottom: 32px;
}

.social-links {
  display: flex;
  justify-content: center;
  gap: 16px;
  margin-bottom: 32px;
}

.social-link {
  width: 44px;
  height: 44px;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 12px;
  background: rgba(255, 255, 255, 0.05);
  border: 1px solid rgba(255, 255, 255, 0.1);
  color: var(--text-secondary);
  transition: all 0.3s ease;
}

.social-link:hover {
  background: rgba(0, 212, 255, 0.1);
  border-color: var(--accent-cyan);
  color: var(--accent-cyan);
  transform: translateY(-3px);
  box-shadow: 0 8px 20px rgba(0, 212, 255, 0.3);
}

.social-link svg {
  width: 20px;
  height: 20px;
}

.scroll-indicator {
  position: absolute;
  bottom: -80px;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 8px;
  opacity: 0.6;
}

.scroll-text {
  font-size: 12px;
  letter-spacing: 0.1em;
  color: var(--text-secondary);
}

.scroll-arrow {
  width: 24px;
  height: 24px;
  animation: bounce 2s ease-in-out infinite;
}

.scroll-arrow svg {
  width: 100%;
  height: 100%;
  color: var(--accent-cyan);
}

@keyframes rotate {
  from { transform: rotate(0deg); }
  to { transform: rotate(360deg); }
}

@keyframes bounce {
  0%, 100% { transform: translateY(0); }
  50% { transform: translateY(8px); }
}

@media (max-width: 768px) {
  .profile-card {
    padding: 32px 24px;
    max-width: 340px;
    margin: 0 16px;
  }

  .avatar-container {
    width: 120px;
    height: 120px;
  }

  .name {
    font-size: 26px;
  }

  .social-links {
    gap: 12px;
  }

  .social-link {
    width: 40px;
    height: 40px;
  }
}
</style>
