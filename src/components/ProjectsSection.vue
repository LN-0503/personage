<template>
  <section id="projects" class="projects-section">
    <div class="section-content">
      <div class="glass-card projects-card">
        <div class="section-header">
          <h2 class="section-title text-gradient">精选项目</h2>
          <div class="title-line"></div>
        </div>
        
        <div class="projects-grid">
          <div 
            v-for="project in projects" 
            :key="project.title"
            class="project-item"
          >
            <div class="project-preview">
              <div class="project-overlay">
                <a :href="project.link" target="_blank" class="project-link">
                  <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                    <path d="M18 13v6a2 2 0 01-2 2H5a2 2 0 01-2-2V8a2 2 0 012-2h6"/>
                    <polyline points="15,3 21,3 21,9"/>
                    <line x1="10" y1="14" x2="21" y2="3"/>
                  </svg>
                  查看项目
                </a>
              </div>
              <div class="project-placeholder">
                <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1">
                  <rect x="3" y="3" width="18" height="18" rx="2" ry="2"/>
                  <circle cx="8.5" cy="8.5" r="1.5"/>
                  <polyline points="21,15 16,10 5,21"/>
                </svg>
              </div>
            </div>
            <div class="project-info">
              <h3 class="project-title">{{ project.title }}</h3>
              <p class="project-desc">{{ project.description }}</p>
              <div class="project-tags">
                <span v-for="tag in project.tags" :key="tag" class="project-tag">
                  {{ tag }}
                </span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'ProjectsSection',
  data() {
    return {
      projects: [
        {
          title: 'AI 智能助手平台',
          description: '基于大语言模型的智能对话系统，支持多轮对话、文件分析和代码生成',
          tags: ['Vue 3', 'Python', 'FastAPI', 'LLM'],
          link: '#'
        },
        {
          title: '实时数据可视化大屏',
          description: '企业级数据监控平台，支持实时数据流处理和多维度可视化分析',
          tags: ['React', 'D3.js', 'WebSocket', 'Kafka'],
          link: '#'
        },
        {
          title: '跨平台电商解决方案',
          description: '高性能电商系统，支持千万级SKU，毫秒级搜索响应',
          tags: ['Next.js', 'Go', 'Elasticsearch', 'Redis'],
          link: '#'
        },
        {
          title: '开发者工具链平台',
          description: '一站式开发者平台，集成CI/CD、监控告警和日志分析',
          tags: ['TypeScript', 'Kubernetes', 'Prometheus', 'Grafana'],
          link: '#'
        }
      ]
    }
  }
}
</script>

<style scoped>
.projects-section {
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 120px 48px;
}

.section-content {
  max-width: 1100px;
  width: 100%;
  position: relative;
  z-index: 10;
}

.projects-card {
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

.projects-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 32px;
}

.project-item {
  background: rgba(255, 255, 255, 0.02);
  border: 1px solid rgba(255, 255, 255, 0.08);
  border-radius: 20px;
  overflow: hidden;
  transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
}

.project-item:hover {
  transform: translateY(-8px);
  border-color: rgba(0, 212, 255, 0.3);
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.3), 0 0 30px rgba(0, 212, 255, 0.1);
}

.project-preview {
  position: relative;
  height: 200px;
  background: linear-gradient(135deg, rgba(0, 212, 255, 0.1), rgba(168, 85, 247, 0.1));
  overflow: hidden;
}

.project-overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.7);
  display: flex;
  align-items: center;
  justify-content: center;
  opacity: 0;
  transition: opacity 0.3s ease;
}

.project-item:hover .project-overlay {
  opacity: 1;
}

.project-link {
  display: flex;
  align-items: center;
  gap: 8px;
  padding: 12px 24px;
  background: var(--accent-cyan);
  color: var(--bg-primary);
  text-decoration: none;
  border-radius: 12px;
  font-weight: 600;
  font-size: 14px;
  transform: translateY(10px);
  transition: transform 0.3s ease;
}

.project-item:hover .project-link {
  transform: translateY(0);
}

.project-link svg {
  width: 18px;
  height: 18px;
}

.project-placeholder {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 80px;
  height: 80px;
  opacity: 0.3;
}

.project-placeholder svg {
  width: 100%;
  height: 100%;
  color: var(--accent-cyan);
}

.project-info {
  padding: 24px;
}

.project-title {
  font-family: 'Orbitron', monospace;
  font-size: 18px;
  font-weight: 600;
  color: var(--text-primary);
  margin-bottom: 12px;
}

.project-desc {
  font-size: 14px;
  color: var(--text-secondary);
  line-height: 1.6;
  margin-bottom: 16px;
}

.project-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
}

.project-tag {
  padding: 4px 10px;
  background: rgba(168, 85, 247, 0.1);
  border: 1px solid rgba(168, 85, 247, 0.3);
  border-radius: 12px;
  font-size: 12px;
  color: var(--accent-purple);
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
  .projects-section {
    padding: 100px 24px;
  }

  .projects-card {
    padding: 40px 24px;
  }

  .section-title {
    font-size: 28px;
  }

  .projects-grid {
    grid-template-columns: 1fr;
    gap: 24px;
  }

  .project-preview {
    height: 160px;
  }
}
</style>
