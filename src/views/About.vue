<template>
  <div class="about-page fade-in">
    <section class="page-banner">
      <div class="container">
        <h1>关于我们</h1>
        <p>十年技术沉淀，助力企业数字化</p>
      </div>
    </section>

    <section class="story-section">
      <div class="container">
        <div class="story-grid">
          <div class="story-content">
            <h2>我们的故事</h2>
            <p>
              科技有限公司成立于2014年，由一群来自互联网大厂的技术骨干和行业资深顾问共同创立。
              我们看到了传统企业在数字化浪潮中的困境，决心用技术的力量帮助他们突破重围。
            </p>
            <p>
              十年来，我们始终坚持"以客户为中心"的理念，深耕企业服务领域，
              先后为超过1000家企业提供了专业的数字化解决方案，涵盖互联网、金融、制造、零售、教育等多个行业。
            </p>
            <p>
              我们相信，技术的价值在于赋能。让每一家企业都能享受到科技带来的红利，是我们不变的使命。
            </p>
          </div>
          <div class="story-image">
            <div class="image-placeholder">🏢</div>
          </div>
        </div>
      </div>
    </section>

    <section class="values-section">
      <div class="container">
        <div class="section-title">
          <h2>核心价值观</h2>
          <p>指引我们前行的信念</p>
        </div>
        <div class="values-grid">
          <div class="value-card">
            <div class="value-icon">🎯</div>
            <h3>客户至上</h3>
            <p>一切从客户需求出发，用心服务每一位客户</p>
          </div>
          <div class="value-card">
            <div class="value-icon">💡</div>
            <h3>创新驱动</h3>
            <p>持续学习新技术，用创新思维解决问题</p>
          </div>
          <div class="value-card">
            <div class="value-icon">🤝</div>
            <h3>团队协作</h3>
            <p>相信团队的力量，共同成长，共同进步</p>
          </div>
          <div class="value-card">
            <div class="value-icon">⚡</div>
            <h3>追求卓越</h3>
            <p>高标准、严要求，交付高质量的产品和服务</p>
          </div>
        </div>
      </div>
    </section>

    <section class="timeline-section">
      <div class="container">
        <div class="section-title">
          <h2>发展历程</h2>
          <p>每一步都在向前</p>
        </div>
        <div class="timeline">
          <div class="timeline-item">
            <div class="timeline-year">2014</div>
            <div class="timeline-content">
              <h3>公司成立</h3>
              <p>科技有限公司在北京正式成立，开始了企业数字化服务之路</p>
            </div>
          </div>
          <div class="timeline-item">
            <div class="timeline-year">2017</div>
            <div class="timeline-content">
              <h3>团队壮大</h3>
              <p>团队规模扩展到30人，服务客户突破200家</p>
            </div>
          </div>
          <div class="timeline-item">
            <div class="timeline-year">2020</div>
            <div class="timeline-content">
              <h3>业务升级</h3>
              <p>推出数据中台和AI产品线，服务客户突破500家</p>
            </div>
          </div>
          <div class="timeline-item">
            <div class="timeline-year">2022</div>
            <div class="timeline-content">
              <h3>总部搬迁</h3>
              <p>总部迁至上海，在深圳、成都设立分公司</p>
            </div>
          </div>
          <div class="timeline-item">
            <div class="timeline-year">2024</div>
            <div class="timeline-content">
              <h3>新的征程</h3>
              <p>服务客户突破1000家，开启AI赋能新篇章</p>
            </div>
          </div>
        </div>
      </div>
    </section>

    <section class="team-section">
      <div class="container">
        <div class="section-title">
          <h2>核心团队</h2>
          <p>一群热爱技术的人</p>
        </div>
        <div class="team-grid">
          <div class="team-card">
            <div class="team-avatar">👨‍💼</div>
            <h3>张明</h3>
            <p class="team-role">CEO · 创始人</p>
            <p class="team-desc">前阿里巴巴高级技术专家，15年互联网行业经验</p>
          </div>
          <div class="team-card">
            <div class="team-avatar">👩‍💼</div>
            <h3>李华</h3>
            <p class="team-role">CTO · 联合创始人</p>
            <p class="team-desc">前腾讯技术总监，10年架构设计经验</p>
          </div>
          <div class="team-card">
            <div class="team-avatar">👨‍💻</div>
            <h3>王强</h3>
            <p class="team-role">产品总监</p>
            <p class="team-desc">前美团产品负责人，8年产品管理经验</p>
          </div>
          <div class="team-card">
            <div class="team-avatar">👩‍🎨</div>
            <h3>陈静</h3>
            <p class="team-role">设计总监</p>
            <p class="team-desc">前字节跳动资深设计师，获多项设计大奖</p>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
</script>

<style scoped>
.page-banner {
  padding: 150px 0 80px;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: #fff;
  text-align: center;
}

.page-banner h1 {
  font-size: 48px;
  margin-bottom: 12px;
}

.page-banner p {
  font-size: 18px;
  opacity: 0.9;
}

.story-section {
  padding: 100px 0;
}

.story-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 60px;
  align-items: center;
}

.story-content h2 {
  font-size: 32px;
  margin-bottom: 24px;
}

.story-content p {
  color: #606266;
  line-height: 1.8;
  margin-bottom: 16px;
}

.image-placeholder {
  width: 100%;
  height: 400px;
  background: linear-gradient(135deg, #e0e7ff 0%, #c7d2fe 100%);
  border-radius: 16px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 120px;
}

.values-section {
  padding: 100px 0;
  background-color: #f8fafc;
}

.values-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 30px;
}

.value-card {
  background-color: #fff;
  padding: 40px 24px;
  border-radius: 12px;
  text-align: center;
  transition: all 0.3s;
}

.value-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 15px 30px rgba(0, 0, 0, 0.08);
}

.value-icon {
  font-size: 48px;
  margin-bottom: 16px;
}

.value-card h3 {
  font-size: 18px;
  margin-bottom: 8px;
}

.value-card p {
  color: #909399;
  font-size: 14px;
}

.timeline-section {
  padding: 100px 0;
}

.timeline {
  position: relative;
  max-width: 800px;
  margin: 0 auto;
}

.timeline::before {
  content: '';
  position: absolute;
  left: 50%;
  top: 0;
  bottom: 0;
  width: 2px;
  background-color: #e4e7ed;
  transform: translateX(-50%);
}

.timeline-item {
  display: flex;
  align-items: center;
  margin-bottom: 50px;
}

.timeline-item:nth-child(odd) {
  flex-direction: row;
}

.timeline-item:nth-child(even) {
  flex-direction: row-reverse;
}

.timeline-year {
  width: 80px;
  height: 80px;
  border-radius: 50%;
  background-color: #409eff;
  color: #fff;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 18px;
  font-weight: 700;
  flex-shrink: 0;
  z-index: 2;
}

.timeline-content {
  width: calc(50% - 60px);
  padding: 20px 24px;
  background-color: #f8fafc;
  border-radius: 8px;
}

.timeline-item:nth-child(odd) .timeline-content {
  margin-left: 40px;
}

.timeline-item:nth-child(even) .timeline-content {
  margin-right: 40px;
}

.timeline-content h3 {
  font-size: 18px;
  margin-bottom: 8px;
  color: #303133;
}

.timeline-content p {
  font-size: 14px;
  color: #909399;
}

.team-section {
  padding: 100px 0;
  background-color: #f8fafc;
}

.team-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 30px;
}

.team-card {
  background-color: #fff;
  padding: 30px;
  border-radius: 12px;
  text-align: center;
  transition: all 0.3s;
}

.team-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 15px 30px rgba(0, 0, 0, 0.08);
}

.team-avatar {
  width: 100px;
  height: 100px;
  border-radius: 50%;
  background-color: #f0f5ff;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 48px;
  margin: 0 auto 16px;
}

.team-card h3 {
  font-size: 18px;
  margin-bottom: 6px;
}

.team-role {
  color: #409eff;
  font-size: 14px;
  margin-bottom: 12px;
}

.team-desc {
  color: #909399;
  font-size: 13px;
  line-height: 1.6;
}

@media (max-width: 768px) {
  .story-grid,
  .team-grid,
  .values-grid {
    grid-template-columns: 1fr;
  }

  .page-banner h1 {
    font-size: 32px;
  }

  .timeline::before {
    left: 20px;
  }

  .timeline-item,
  .timeline-item:nth-child(even) {
    flex-direction: row;
  }

  .timeline-content,
  .timeline-item:nth-child(odd) .timeline-content,
  .timeline-item:nth-child(even) .timeline-content {
    width: calc(100% - 120px);
    margin-left: 40px;
    margin-right: 0;
  }
}
</style>