<template>
  <div class="home-page fade-in">
    <section class="hero-section">
      <div class="hero-bg"></div>
      <div class="container hero-content">
        <h1 class="hero-title">
          用科技赋能企业<br />
          <span>数字化转型</span>
        </h1>
        <p class="hero-desc">
          我们是一家专注于企业数字化解决方案的科技公司，
          <br />帮助传统企业快速拥抱互联网，实现业务增长。
        </p>
        <div class="hero-actions">
          <router-link to="/contact" class="btn btn-primary">免费咨询</router-link>
          <router-link to="/services" class="btn btn-outline">了解更多</router-link>
        </div>
      </div>
      <div class="scroll-hint">
        <span></span>
        <span></span>
        <span></span>
      </div>
    </section>

    <section class="about-section">
      <div class="container">
        <div class="section-title">
          <h2>关于我们</h2>
          <p>十年磨一剑，专注企业数字化</p>
        </div>
        <div class="about-grid">
          <div class="about-text">
            <h3>做最懂企业的技术服务商</h3>
            <p>
              我们成立于2014年，始终坚持"以客户为中心"的理念，
              已为超过1000家企业提供了专业的数字化解决方案。
            </p>
            <p>
              团队汇聚了来自互联网大厂的技术专家和行业资深顾问，
              用技术驱动商业，让每一家企业都能享受到科技带来的红利。
            </p>
            <ul class="about-features">
              <li>✅ 10年行业经验</li>
              <li>✅ 1000+企业服务</li>
              <li>✅ 98%客户满意度</li>
            </ul>
          </div>
          <div class="about-image">
            <div class="image-placeholder">
              <span>🏢</span>
            </div>
          </div>
        </div>
      </div>
    </section>

    <section class="services-section">
      <div class="container">
        <div class="section-title">
          <h2>产品服务</h2>
          <p>全方位的企业数字化解决方案</p>
        </div>
        <div class="services-grid">
          <div class="service-card">
            <div class="service-icon">💻</div>
            <h3>网站建设</h3>
            <p>企业官网、电商平台、门户系统，专业设计定制开发</p>
            <router-link to="/services" class="service-link">了解更多 →</router-link>
          </div>
          <div class="service-card">
            <div class="service-icon">📱</div>
            <h3>小程序开发</h3>
            <p>微信小程序、支付宝小程序，轻量化获客工具</p>
            <router-link to="/services" class="service-link">了解更多 →</router-link>
          </div>
          <div class="service-card">
            <div class="service-icon">📊</div>
            <h3>数据中台</h3>
            <p>数据采集、分析、可视化，让数据驱动决策</p>
            <router-link to="/services" class="service-link">了解更多 →</router-link>
          </div>
          <div class="service-card">
            <div class="service-icon">🤖</div>
            <h3>AI应用</h3>
            <p>智能客服、内容生成、图像识别，AI赋能业务</p>
            <router-link to="/services" class="service-link">了解更多 →</router-link>
          </div>
          <div class="service-card">
            <div class="service-icon">☁️</div>
            <h3>云服务</h3>
            <p>云迁移、云托管、云安全，一站式上云方案</p>
            <router-link to="/services" class="service-link">了解更多 →</router-link>
          </div>
          <div class="service-card">
            <div class="service-icon">🔧</div>
            <h3>技术咨询</h3>
            <p>架构设计、技术选型、团队培训，专业咨询服务</p>
            <router-link to="/services" class="service-link">了解更多 →</router-link>
          </div>
        </div>
      </div>
    </section>

    <section class="stats-section">
      <div class="container">
        <div class="stats-grid">
          <div class="stat-item">
            <div class="stat-number">1000+</div>
            <div class="stat-label">服务企业</div>
          </div>
          <div class="stat-item">
            <div class="stat-number">10+</div>
            <div class="stat-label">行业经验</div>
          </div>
          <div class="stat-item">
            <div class="stat-number">50+</div>
            <div class="stat-label">技术专家</div>
          </div>
          <div class="stat-item">
            <div class="stat-number">98%</div>
            <div class="stat-label">客户满意</div>
          </div>
        </div>
      </div>
    </section>

    <section class="news-section">
      <div class="container">
        <div class="section-title">
          <h2>最新动态</h2>
          <p>了解我们的最新资讯和行业洞察</p>
        </div>
        <div class="news-grid">
          <div class="news-card">
            <div class="news-image">📰</div>
            <div class="news-content">
              <span class="news-date">2024-01-15</span>
              <h3>公司荣获2023年度最佳技术服务商</h3>
              <p>我们凭借卓越的技术实力和优质的客户服务，荣获行业权威奖项...</p>
              <router-link to="/news" class="news-link">阅读全文 →</router-link>
            </div>
          </div>
          <div class="news-card">
            <div class="news-image">🚀</div>
            <div class="news-content">
              <span class="news-date">2024-01-10</span>
              <h3>新产品发布：智能数据分析平台2.0</h3>
              <p>全新升级的数据平台，更强大的分析能力，更直观的数据可视化...</p>
              <router-link to="/news" class="news-link">阅读全文 →</router-link>
            </div>
          </div>
          <div class="news-card">
            <div class="news-image">💡</div>
            <div class="news-content">
              <span class="news-date">2024-01-05</span>
              <h3>AI如何改变中小企业的运营模式</h3>
              <p>从智能客服到自动化营销，AI正在重塑企业的每一个运营环节...</p>
              <router-link to="/news" class="news-link">阅读全文 →</router-link>
            </div>
          </div>
        </div>
      </div>
    </section>

    <section class="cta-section">
      <div class="container">
        <div class="cta-content">
          <h2>准备好开启数字化转型了吗？</h2>
          <p>免费咨询，让我们的专家为您量身定制方案</p>
          <router-link to="/contact" class="btn btn-primary">立即咨询</router-link>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
</script>

<style scoped>
.hero-section {
  position: relative;
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
}

.hero-bg {
  position: absolute;
  inset: 0;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  opacity: 0.95;
}

.hero-bg::before {
  content: '';
  position: absolute;
  inset: 0;
  background-image: 
    radial-gradient(circle at 20% 80%, rgba(255,255,255,0.15) 0%, transparent 50%),
    radial-gradient(circle at 80% 20%, rgba(255,255,255,0.15) 0%, transparent 50%);
}

.hero-content {
  position: relative;
  text-align: center;
  color: #fff;
  z-index: 2;
  padding-top: 70px;
}

.hero-title {
  font-size: 56px;
  font-weight: 700;
  margin-bottom: 24px;
  line-height: 1.3;
}

.hero-title span {
  background: linear-gradient(90deg, #ffd700, #ffed4e);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.hero-desc {
  font-size: 18px;
  margin-bottom: 40px;
  opacity: 0.9;
}

.hero-actions {
  display: flex;
  gap: 16px;
  justify-content: center;
}

.hero-actions .btn-primary {
  background-color: #fff;
  color: #409eff;
}

.hero-actions .btn-primary:hover {
  background-color: #f0f0f0;
  transform: translateY(-2px);
}

.hero-actions .btn-outline {
  border-color: #fff;
  color: #fff;
}

.hero-actions .btn-outline:hover {
  background-color: rgba(255, 255, 255, 0.2);
  border-color: #fff;
}

.scroll-hint {
  position: absolute;
  bottom: 30px;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  flex-direction: column;
  gap: 6px;
  z-index: 2;
}

.scroll-hint span {
  width: 8px;
  height: 8px;
  border-radius: 50%;
  background-color: rgba(255, 255, 255, 0.6);
  animation: bounce 1.5s infinite;
}

.scroll-hint span:nth-child(2) {
  animation-delay: 0.2s;
}

.scroll-hint span:nth-child(3) {
  animation-delay: 0.4s;
}

@keyframes bounce {
  0%, 100% { transform: translateY(0); opacity: 0.6; }
  50% { transform: translateY(10px); opacity: 1; }
}

.about-section {
  padding: 100px 0;
}

.about-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 60px;
  align-items: center;
}

.about-text h3 {
  font-size: 28px;
  margin-bottom: 20px;
  color: #303133;
}

.about-text p {
  color: #606266;
  line-height: 1.8;
  margin-bottom: 16px;
}

.about-features {
  margin-top: 20px;
}

.about-features li {
  padding: 8px 0;
  color: #606266;
  font-weight: 500;
}

.about-image {
  display: flex;
  justify-content: center;
}

.image-placeholder {
  width: 100%;
  height: 350px;
  background: linear-gradient(135deg, #e0e7ff 0%, #c7d2fe 100%);
  border-radius: 16px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 100px;
}

.services-section {
  padding: 100px 0;
  background-color: #f8fafc;
}

.services-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 30px;
}

.service-card {
  background-color: #fff;
  padding: 40px 30px;
  border-radius: 12px;
  transition: all 0.3s;
  border: 1px solid #f0f0f0;
}

.service-card:hover {
  transform: translateY(-10px);
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.1);
  border-color: #409eff;
}

.service-icon {
  font-size: 48px;
  margin-bottom: 20px;
}

.service-card h3 {
  font-size: 20px;
  margin-bottom: 12px;
  color: #303133;
}

.service-card p {
  color: #909399;
  margin-bottom: 16px;
  line-height: 1.6;
}

.service-link {
  color: #409eff;
  font-weight: 500;
  transition: all 0.3s;
}

.service-link:hover {
  color: #66b1ff;
}

.stats-section {
  padding: 80px 0;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
}

.stats-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 40px;
}

.stat-item {
  text-align: center;
  color: #fff;
}

.stat-number {
  font-size: 48px;
  font-weight: 700;
  margin-bottom: 8px;
}

.stat-label {
  font-size: 16px;
  opacity: 0.9;
}

.news-section {
  padding: 100px 0;
}

.news-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 30px;
}

.news-card {
  background-color: #fff;
  border-radius: 12px;
  overflow: hidden;
  border: 1px solid #f0f0f0;
  transition: all 0.3s;
}

.news-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 15px 30px rgba(0, 0, 0, 0.08);
}

.news-image {
  height: 180px;
  background: linear-gradient(135deg, #f5f7fa 0%, #e4e7ed 100%);
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 60px;
}

.news-content {
  padding: 24px;
}

.news-date {
  font-size: 13px;
  color: #909399;
  margin-bottom: 10px;
  display: block;
}

.news-content h3 {
  font-size: 18px;
  margin-bottom: 10px;
  color: #303133;
  line-height: 1.5;
}

.news-content p {
  color: #909399;
  font-size: 14px;
  margin-bottom: 12px;
  line-height: 1.6;
}

.news-link {
  color: #409eff;
  font-size: 14px;
  font-weight: 500;
}

.cta-section {
  padding: 80px 0;
  background: linear-gradient(135deg, #409eff 0%, #66b1ff 100%);
}

.cta-content {
  text-align: center;
  color: #fff;
}

.cta-content h2 {
  font-size: 32px;
  margin-bottom: 12px;
}

.cta-content p {
  font-size: 16px;
  margin-bottom: 32px;
  opacity: 0.9;
}

.cta-content .btn-primary {
  background-color: #fff;
  color: #409eff;
}

.cta-content .btn-primary:hover {
  background-color: #f0f0f0;
}

@media (max-width: 768px) {
  .hero-title {
    font-size: 36px;
  }

  .about-grid {
    grid-template-columns: 1fr;
  }

  .services-grid {
    grid-template-columns: repeat(2, 1fr);
  }

  .stats-grid {
    grid-template-columns: repeat(2, 1fr);
  }

  .news-grid {
    grid-template-columns: 1fr;
  }

  .hero-actions {
    flex-direction: column;
    align-items: center;
  }
}

@media (max-width: 480px) {
  .services-grid {
    grid-template-columns: 1fr;
  }
}
</style>