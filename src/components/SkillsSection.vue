<template>
  <section id="skills" class="skills-section">
    <div class="section-content">
      <div class="glass-card skills-card">
        <div class="section-header">
          <h2 class="section-title text-gradient">技能专长</h2>
          <div class="title-line"></div>
        </div>
        
        <div class="skills-grid">
          <div v-for="category in skillCategories" :key="category.name" class="skill-category">
            <h3 class="category-title">{{ category.name }}</h3>
            <div class="skills-list">
              <div 
                v-for="skill in category.skills" 
                :key="skill.name"
                class="skill-item"
              >
                <div class="skill-header">
                  <span class="skill-name">{{ skill.name }}</span>
                  <span class="skill-level">{{ skill.level }}%</span>
                </div>
                <div class="skill-bar">
                  <div 
                    class="skill-progress" 
                    :style="{ width: skill.level + '%' }"
                  ></div>
                </div>
              </div>
            </div>
          </div>
        </div>
        
        <div class="tech-tags">
          <span v-for="tech in techStack" :key="tech" class="tech-tag">
            {{ tech }}
          </span>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'SkillsSection',
  data() {
    return {
      skillCategories: [
        {
          name: '前端开发',
          skills: [
            { name: 'Vue / React', level: 95 },
            { name: 'TypeScript', level: 90 },
            { name: 'CSS / SCSS', level: 92 },
            { name: 'Node.js', level: 85 }
          ]
        },
        {
          name: '后端开发',
          skills: [
            { name: 'Python', level: 88 },
            { name: 'Go', level: 75 },
            { name: 'PostgreSQL', level: 85 },
            { name: 'Redis', level: 80 }
          ]
        },
        {
          name: '工具&其他',
          skills: [
            { name: 'Git / Docker', level: 90 },
            { name: 'AWS / GCP', level: 82 },
            { name: 'CI/CD', level: 85 },
            { name: 'Linux', level: 78 }
          ]
        }
      ],
      techStack: [
        'Vue 3', 'React', 'TypeScript', 'Node.js', 'Python', 'Go',
        'PostgreSQL', 'MongoDB', 'Redis', 'Docker', 'Kubernetes',
        'AWS', 'GraphQL', 'REST API', 'WebSocket', 'Tailwind CSS'
      ]
    }
  }
}
</script>

<style scoped>
.skills-section {
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 120px 48px;
}

.section-content {
  max-width: 1000px;
  width: 100%;
  position: relative;
  z-index: 10;
}

.skills-card {
  padding: 64px;
  animation: fade-up 0.8s ease-out;
}

.section-header {
  text-align: center;
  margin-bottom: 48px;
}

.section-title {
  font-family: 'Orbitron', monospace;
  font-size: 36px;
  font-weight: 700;
  letter-spacing: 0.1em;
  margin-bottom: 16px;
}

.title-line {
  width: 80px;
  height: 3px;
  background: linear-gradient(90deg, var(--accent-cyan), var(--accent-purple));
  margin: 0 auto;
  border-radius: 2px;
}

.skills-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 40px;
  margin-bottom: 48px;
}

.category-title {
  font-family: 'Orbitron', monospace;
  font-size: 16px;
  font-weight: 600;
  color: var(--accent-cyan);
  margin-bottom: 20px;
  letter-spacing: 0.05em;
}

.skills-list {
  display: flex;
  flex-direction: column;
  gap: 16px;
}

.skill-item {
  background: rgba(255, 255, 255, 0.02);
  padding: 12px 16px;
  border-radius: 12px;
  border: 1px solid rgba(255, 255, 255, 0.05);
  transition: all 0.3s ease;
}

.skill-item:hover {
  background: rgba(0, 212, 255, 0.05);
  border-color: rgba(0, 212, 255, 0.2);
  transform: translateX(5px);
}

.skill-header {
  display: flex;
  justify-content: space-between;
  margin-bottom: 8px;
}

.skill-name {
  font-size: 14px;
  color: var(--text-primary);
  font-weight: 500;
}

.skill-level {
  font-size: 12px;
  color: var(--accent-cyan);
  font-family: 'Orbitron', monospace;
}

.skill-bar {
  height: 4px;
  background: rgba(255, 255, 255, 0.1);
  border-radius: 2px;
  overflow: hidden;
}

.skill-progress {
  height: 100%;
  background: linear-gradient(90deg, var(--accent-cyan), var(--accent-purple));
  border-radius: 2px;
  transition: width 1s ease-out;
  box-shadow: 0 0 10px var(--glow-cyan);
}

.tech-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 12px;
  justify-content: center;
  padding-top: 32px;
  border-top: 1px solid var(--glass-border);
}

.tech-tag {
  padding: 8px 16px;
  background: rgba(255, 255, 255, 0.03);
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 20px;
  font-size: 13px;
  color: var(--text-secondary);
  transition: all 0.3s ease;
}

.tech-tag:hover {
  background: rgba(168, 85, 247, 0.1);
  border-color: var(--accent-purple);
  color: var(--accent-purple);
  transform: translateY(-2px);
}

@keyframes fade-up {
  from {
    opacity: 0;
    transform: translateY(30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@media (max-width: 768px) {
  .skills-section {
    padding: 100px 24px;
  }

  .skills-card {
    padding: 40px 24px;
  }

  .section-title {
    font-size: 28px;
  }

  .skills-grid {
    grid-template-columns: 1fr;
    gap: 32px;
  }
}
</style>
