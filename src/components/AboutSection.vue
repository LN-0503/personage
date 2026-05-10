<template>
  <section id="about" class="about-section">
    <div class="section-content">
      <div class="glass-card about-card">
        <div class="section-header">
          <h2 class="section-title text-gradient">关于我</h2>
          <div class="title-line"></div>
        </div>
        
        <div class="about-grid">
          <div class="about-text">
            <p class="bio">
              你好！我是林逸尘，一名热爱技术、追求极致的全栈开发工程师。
              专注于创造优雅、高效的数字体验，将复杂的技术转化为简洁优美的解决方案。
            </p>
            <p class="bio">
              在过去的五年里，我有幸参与过多个创新项目，从零开始构建了多个成功的应用。
              我相信好的代码不仅要能运行，更要像诗一样优美。
            </p>
          </div>
          
          <div class="stats-grid">
            <div class="stat-item">
              <span class="stat-number text-gradient">5+</span>
              <span class="stat-label">年开发经验</span>
            </div>
            <div class="stat-item">
              <span class="stat-number text-gradient">50+</span>
              <span class="stat-label">完成项目</span>
            </div>
            <div class="stat-item">
              <span class="stat-number text-gradient">20+</span>
              <span class="stat-label">技术栈掌握</span>
            </div>
            <div class="stat-item">
              <span class="stat-number text-gradient">∞</span>
              <span class="stat-label">持续学习</span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'AboutSection'
}
</script>

<style scoped>
.about-section {
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 120px 48px;
}

.section-content {
  max-width: 900px;
  width: 100%;
  position: relative;
  z-index: 10;
}

.about-card {
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

.about-grid {
  display: grid;
  gap: 48px;
}

.bio {
  font-size: 16px;
  line-height: 1.8;
  color: var(--text-secondary);
  margin-bottom: 20px;
}

.bio:last-child {
  margin-bottom: 0;
}

.stats-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 24px;
  padding-top: 32px;
  border-top: 1px solid var(--glass-border);
}

.stat-item {
  text-align: center;
}

.stat-number {
  font-family: 'Orbitron', monospace;
  font-size: 40px;
  font-weight: 700;
  display: block;
  margin-bottom: 8px;
}

.stat-label {
  font-size: 14px;
  color: var(--text-secondary);
  letter-spacing: 0.05em;
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
  .about-section {
    padding: 100px 24px;
  }

  .about-card {
    padding: 40px 24px;
  }

  .section-title {
    font-size: 28px;
  }

  .stats-grid {
    grid-template-columns: repeat(2, 1fr);
  }

  .stat-number {
    font-size: 32px;
  }
}
</style>
