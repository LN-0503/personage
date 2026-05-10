<template>
  <div id="app">
    <ParticleBackground />
    <FlowLines />
    <GlowOrbs />
    <GlassNavbar :sections="sections" :currentSection="currentSection" @navigate="scrollToSection" />
    <main class="main-content">
      <HeroSection :profile="profile" />
      <AboutSection id="about" />
      <SkillsSection id="skills" />
      <ProjectsSection id="projects" />
      <ContactSection id="contact" />
    </main>
    <SideNavigation :sections="sections" :currentSection="currentSection" @navigate="scrollToSection" />
  </div>
</template>

<script>
import ParticleBackground from './components/ParticleBackground.vue'
import FlowLines from './components/FlowLines.vue'
import GlowOrbs from './components/GlowOrbs.vue'
import GlassNavbar from './components/GlassNavbar.vue'
import SideNavigation from './components/SideNavigation.vue'
import HeroSection from './components/HeroSection.vue'
import AboutSection from './components/AboutSection.vue'
import SkillsSection from './components/SkillsSection.vue'
import ProjectsSection from './components/ProjectsSection.vue'
import ContactSection from './components/ContactSection.vue'

export default {
  name: 'App',
  components: {
    ParticleBackground,
    FlowLines,
    GlowOrbs,
    GlassNavbar,
    SideNavigation,
    HeroSection,
    AboutSection,
    SkillsSection,
    ProjectsSection,
    ContactSection
  },
  data() {
    return {
      currentSection: 'home',
      sections: [
        { id: 'home', name: '首页', icon: 'home' },
        { id: 'about', name: '关于', icon: 'user' },
        { id: 'skills', name: '技能', icon: 'code' },
        { id: 'projects', name: '项目', icon: 'folder' },
        { id: 'contact', name: '联系', icon: 'mail' }
      ],
      profile: {
        name: '林逸尘',
        title: '全栈开发工程师',
        subtitle: '创造数字未来的艺术家',
        avatar: 'https://images.unsplash.com/photo-1507003211169-0a1dd7228f2d?w=300&h=300&fit=crop&crop=face',
        socials: [
          { platform: 'github', url: 'https://github.com', icon: 'github' },
          { platform: 'twitter', url: 'https://twitter.com', icon: 'twitter' },
          { platform: 'linkedin', url: 'https://linkedin.com', icon: 'linkedin' },
          { platform: 'mail', url: 'mailto:@example@domain.com', icon: 'mail' }
        ]
      }
    }
  },
  mounted() {
    this.setupScrollObserver()
    window.addEventListener('scroll', this.handleScroll)
  },
  beforeDestroy() {
    window.removeEventListener('scroll', this.handleScroll)
  },
  methods: {
    scrollToSection(sectionId) {
      const element = document.getElementById(sectionId)
      if (element) {
        element.scrollIntoView({ behavior: 'smooth' })
        this.currentSection = sectionId
      }
    },
    handleScroll() {
      const scrollPosition = window.scrollY + window.innerHeight / 2
      const sections = document.querySelectorAll('section[id]')
      
      sections.forEach(section => {
        const sectionTop = section.offsetTop
        const sectionHeight = section.offsetHeight
        if (scrollPosition >= sectionTop && scrollPosition < sectionTop + sectionHeight) {
          this.currentSection = section.getAttribute('id')
        }
      })
    },
    setupScrollObserver() {
      const options = {
        root: null,
        rootMargin: '0px',
        threshold: 0.3
      }

      const observer = new IntersectionObserver((entries) => {
        entries.forEach(entry => {
          if (entry.isIntersecting) {
            this.currentSection = entry.target.getAttribute('id')
          }
        })
      }, options)

      document.querySelectorAll('section[id]').forEach(section => {
        observer.observe(section)
      })
    }
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

:root {
  --bg-primary: #0a0a0f;
  --bg-secondary: #12121a;
  --accent-cyan: #00d4ff;
  --accent-purple: #a855f7;
  --accent-pink: #ec4899;
  --text-primary: #ffffff;
  --text-secondary: rgba(255, 255, 255, 0.7);
  --glass-bg: rgba(255, 255, 255, 0.05);
  --glass-border: rgba(255, 255, 255, 0.1);
  --glow-cyan: rgba(0, 212, 255, 0.5);
  --glow-purple: rgba(168, 85, 247, 0.5);
}

html {
  scroll-behavior: smooth;
}

body {
  font-family: 'Inter', system-ui, -apple-system, sans-serif;
  background-color: var(--bg-primary);
  color: var(--text-primary);
  line-height: 1.6;
  overflow-x: hidden;
}

#app {
  min-height: 100vh;
  position: relative;
}

.main-content {
  position: relative;
  z-index: 10;
}

section {
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 80px 48px;
  position: relative;
}

.glass-card {
  background: var(--glass-bg);
  backdrop-filter: blur(20px);
  -webkit-backdrop-filter: blur(20px);
  border: 1px solid var(--glass-border);
  border-radius: 24px;
}

@keyframes float {
  0%, 100% {
    transform: translateY(0px);
  }
  50% {
    transform: translateY(-10px);
  }
}

@keyframes pulse-glow {
  0%, 100% {
    opacity: 0.6;
  }
  50% {
    opacity: 1;
  }
}

@keyframes gradient-shift {
  0% {
    background-position: 0% 50%;
  }
  50% {
    background-position: 100% 50%;
  }
  100% {
    background-position: 0% 50%;
  }
}

.text-gradient {
  background: linear-gradient(135deg, var(--accent-cyan), var(--accent-purple), var(--accent-pink));
  background-size: 200% 200%;
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
  animation: gradient-shift 4s ease infinite;
}

.text-glow {
  text-shadow: 
    0 0 10px var(--glow-cyan),
    0 0 20px var(--glow-cyan),
    0 0 40px var(--glow-purple);
}

@media (max-width: 768px) {
  section {
    padding: 60px 24px;
  }
}
</style>
