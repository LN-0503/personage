<template>
  <section id="contact" class="contact-section">
    <div class="section-content">
      <div class="glass-card contact-card">
        <div class="section-header">
          <h2 class="section-title text-gradient">联系我</h2>
          <div class="title-line"></div>
          <p class="section-subtitle">开启合作之旅</p>
        </div>
        
        <div class="contact-grid">
          <div class="contact-info">
            <div class="info-item">
              <div class="info-icon">
                <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
                  <path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"/>
                  <polyline points="22,6 12,13 2,6"/>
                </svg>
              </div>
              <div class="info-content">
                <span class="info-label">电子邮件</span>
                <span class="info-value">hello@example.com</span>
              </div>
            </div>
            
            <div class="info-item">
              <div class="info-icon">
                <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
                  <path d="M21 10c0 7-9 13-9 13s-9-6-9-13a9 9 0 0118 0z"/>
                  <circle cx="12" cy="10" r="3"/>
                </svg>
              </div>
              <div class="info-content">
                <span class="info-label">所在地</span>
                <span class="info-value">中国 · 上海</span>
              </div>
            </div>
            
            <div class="info-item">
              <div class="info-icon">
                <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
                  <circle cx="12" cy="12" r="10"/>
                  <polyline points="12,6 12,12 16,14"/>
                </svg>
              </div>
              <div class="info-content">
                <span class="info-label">响应时间</span>
                <span class="info-value">24 小时内</span>
              </div>
            </div>
          </div>
          
          <form class="contact-form" @submit.prevent="handleSubmit">
            <div class="form-group">
              <input 
                v-model="form.name"
                type="text" 
                class="form-input" 
                placeholder="您的姓名"
                required
              />
            </div>
            <div class="form-group">
              <input 
                v-model="form.email"
                type="email" 
                class="form-input" 
                placeholder="电子邮箱"
                required
              />
            </div>
            <div class="form-group">
              <textarea 
                v-model="form.message"
                class="form-input form-textarea" 
                placeholder="想要说的话..."
                rows="5"
                required
              ></textarea>
            </div>
            <button type="submit" class="submit-btn" :class="{ loading: isSubmitting }">
              <span v-if="!isSubmitting">发送消息</span>
              <span v-else class="loading-text">发送中...</span>
            </button>
          </form>
        </div>
        
        <div class="social-links">
          <a href="https://github.com" target="_blank" class="social-link" aria-label="GitHub">
            <svg viewBox="0 0 24 24" fill="currentColor">
              <path d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/>
            </svg>
          </a>
          <a href="https://twitter.com" target="_blank" class="social-link" aria-label="Twitter">
            <svg viewBox="0 0 24 24" fill="currentColor">
              <path d="M18.244 2.25h3.308l-7.227 8.26 8.502 11.24H16.17l-5.214-6.817L4.99 21.75H1.68l7.73-8.835L1.254 2.25H8.08l4.713 6.231zm-1.161 17.52h1.833L7.084 4.126H5.117z"/>
            </svg>
          </a>
          <a href="https://linkedin.com" target="_blank" class="social-link" aria-label="LinkedIn">
            <svg viewBox="0 0 24 24" fill="currentColor">
              <path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433c-1.144 0-2.063-.926-2.063-2.065 0-1.138.92-2.063 2.063-2.063 1.14 0 2.064.925 2.064 2.063 0 1.139-.925 2.065-2.064 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/>
            </svg>
          </a>
        </div>
        
        <div v-if="submitSuccess" class="success-message">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
            <polyline points="20,6 9,17 4,12"/>
          </svg>
          消息发送成功！
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'ContactSection',
  data() {
    return {
      form: {
        name: '',
        email: '',
        message: ''
      },
      isSubmitting: false,
      submitSuccess: false
    }
  },
  methods: {
    async handleSubmit() {
      this.isSubmitting = true
      await new Promise(resolve => setTimeout(resolve, 1500))
      this.isSubmitting = false
      this.submitSuccess = true
      this.form = { name: '', email: '', message: '' }
      setTimeout(() => {
        this.submitSuccess = false
      }, 3000)
    }
  }
}
</script>

<style scoped>
.contact-section {
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

.contact-card {
  padding: 64px;
  animation: fade-up 0.8s ease-out;
  text-align: center;
}

.section-header {
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
  margin: 0 auto 16px;
  border-radius: 2px;
}

.section-subtitle {
  font-size: 16px;
  color: var(--text-secondary);
}

.contact-grid {
  display: grid;
  grid-template-columns: 1fr 1.5fr;
  gap: 48px;
  margin-bottom: 48px;
  text-align: left;
}

.contact-info {
  display: flex;
  flex-direction: column;
  gap: 24px;
}

.info-item {
  display: flex;
  align-items: flex-start;
  gap: 16px;
  padding: 16px;
  background: rgba(255, 255, 255, 0.02);
  border: 1px solid rgba(255, 255, 255, 0.05);
  border-radius: 16px;
  transition: all 0.3s ease;
}

.info-item:hover {
  background: rgba(0, 212, 255, 0.05);
  border-color: rgba(0, 212, 255, 0.2);
}

.info-icon {
  width: 40px;
  height: 40px;
  display: flex;
  align-items: center;
  justify-content: center;
  background: linear-gradient(135deg, var(--accent-cyan), var(--accent-purple));
  border-radius: 10px;
  flex-shrink: 0;
}

.info-icon svg {
  width: 20px;
  height: 20px;
  color: white;
}

.info-content {
  display: flex;
  flex-direction: column;
  gap: 4px;
}

.info-label {
  font-size: 12px;
  color: var(--text-secondary);
  text-transform: uppercase;
  letter-spacing: 0.1em;
}

.info-value {
  font-size: 14px;
  color: var(--text-primary);
  font-weight: 500;
}

.contact-form {
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.form-group {
  width: 100%;
}

.form-input {
  width: 100%;
  padding: 16px 20px;
  background: rgba(255, 255, 255, 0.03);
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 12px;
  color: var(--text-primary);
  font-size: 14px;
  font-family: inherit;
  transition: all 0.3s ease;
  outline: none;
}

.form-input::placeholder {
  color: var(--text-secondary);
  opacity: 0.6;
}

.form-input:focus {
  background: rgba(0, 212, 255, 0.05);
  border-color: var(--accent-cyan);
  box-shadow: 0 0 20px rgba(0, 212, 255, 0.1);
}

.form-textarea {
  resize: vertical;
  min-height: 120px;
}

.submit-btn {
  padding: 16px 32px;
  background: linear-gradient(135deg, var(--accent-cyan), var(--accent-purple));
  border: none;
  border-radius: 12px;
  color: white;
  font-size: 16px;
  font-weight: 600;
  font-family: inherit;
  cursor: pointer;
  transition: all 0.3s ease;
  position: relative;
  overflow: hidden;
}

.submit-btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 10px 30px rgba(0, 212, 255, 0.3);
}

.submit-btn.loading {
  opacity: 0.8;
  cursor: not-allowed;
}

.social-links {
  display: flex;
  justify-content: center;
  gap: 16px;
  padding-top: 32px;
  border-top: 1px solid var(--glass-border);
}

.social-link {
  width: 48px;
  height: 48px;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 14px;
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
}

.social-link svg {
  width: 22px;
  height: 22px;
}

.success-message {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 10px;
  margin-top: 24px;
  padding: 16px;
  background: rgba(0, 212, 255, 0.1);
  border: 1px solid var(--accent-cyan);
  border-radius: 12px;
  color: var(--accent-cyan);
  font-weight: 500;
  animation: fade-in 0.3s ease;
}

.success-message svg {
  width: 20px;
  height: 20px;
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

@keyframes fade-in {
  from { opacity: 0; }
  to { opacity: 1; }
}

@media (max-width: 768px) {
  .contact-section {
    padding: 100px 24px;
  }

  .contact-card {
    padding: 40px 24px;
  }

  .section-title {
    font-size: 28px;
  }

  .contact-grid {
    grid-template-columns: 1fr;
    gap: 32px;
  }

  .info-item {
    padding: 12px;
  }
}
</style>
