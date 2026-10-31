<template>
  <div class="contact-page fade-in">
    <section class="page-banner">
      <div class="container">
        <h1>联系我们</h1>
        <p>期待与您的合作</p>
      </div>
    </section>

    <section class="contact-section">
      <div class="container">
        <div class="contact-grid">
          <div class="contact-info">
            <h2>联系方式</h2>
            <p class="contact-desc">
              如果您有任何问题或合作意向，欢迎通过以下方式联系我们。
              我们的团队会在24小时内回复您。
            </p>
            <div class="info-list">
              <div class="info-item">
                <span class="info-icon">📞</span>
                <div>
                  <h4>电话咨询</h4>
                  <p>400-888-8888</p>
                  <span>周一至周五 9:00-18:00</span>
                </div>
              </div>
              <div class="info-item">
                <span class="info-icon">📧</span>
                <div>
                  <h4>邮箱</h4>
                  <p>contact@company.com</p>
                  <span>24小时内回复</span>
                </div>
              </div>
              <div class="info-item">
                <span class="info-icon">📍</span>
                <div>
                  <h4>公司地址</h4>
                  <p>北京市朝阳区科技园区</p>
                  <span>欢迎来公司拜访</span>
                </div>
              </div>
              <div class="info-item">
                <span class="info-icon">💬</span>
                <div>
                  <h4>在线客服</h4>
                  <p>QQ: 123456789</p>
                  <span>微信: company-official</span>
                </div>
              </div>
            </div>
          </div>

          <div class="contact-form-wrapper">
            <h2>在线留言</h2>
            <form class="contact-form" @submit.prevent="handleSubmit">
              <div class="form-row">
                <div class="form-item">
                  <label>姓名 *</label>
                  <input type="text" v-model="form.name" placeholder="请输入您的姓名" required />
                </div>
                <div class="form-item">
                  <label>电话 *</label>
                  <input type="tel" v-model="form.phone" placeholder="请输入您的电话" required />
                </div>
              </div>
              <div class="form-item">
                <label>邮箱</label>
                <input type="email" v-model="form.email" placeholder="请输入您的邮箱" />
              </div>
              <div class="form-item">
                <label>公司名称</label>
                <input type="text" v-model="form.company" placeholder="请输入公司名称" />
              </div>
              <div class="form-item">
                <label>咨询类型</label>
                <select v-model="form.type">
                  <option value="">请选择咨询类型</option>
                  <option value="website">网站建设</option>
                  <option value="miniapp">小程序开发</option>
                  <option value="data">数据中台</option>
                  <option value="ai">AI应用</option>
                  <option value="other">其他</option>
                </select>
              </div>
              <div class="form-item">
                <label>留言内容 *</label>
                <textarea v-model="form.message" placeholder="请描述您的需求或问题..." rows="5" required></textarea>
              </div>
              <button type="submit" class="btn btn-primary submit-btn">提交留言</button>
            </form>
          </div>
        </div>
      </div>
    </section>

    <section class="map-section">
      <div class="container">
        <div class="map-placeholder">
          <span>🗺️</span>
          <p>地图位置（此处可接入高德/百度地图）</p>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
import { reactive } from 'vue'

const form = reactive({
  name: '',
  phone: '',
  email: '',
  company: '',
  type: '',
  message: ''
})

const handleSubmit = () => {
  const messages = JSON.parse(localStorage.getItem('contact_messages') || '[]')
  messages.unshift({
    id: Date.now(),
    ...form,
    time: new Date().toLocaleString()
  })
  localStorage.setItem('contact_messages', JSON.stringify(messages))
  alert('✅ 留言提交成功！\n\n我们会尽快与您联系。')
  Object.assign(form, {
    name: '',
    phone: '',
    email: '',
    company: '',
    type: '',
    message: ''
  })
}
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

.contact-section {
  padding: 80px 0;
}

.contact-grid {
  display: grid;
  grid-template-columns: 1fr 1.2fr;
  gap: 60px;
}

.contact-info h2,
.contact-form-wrapper h2 {
  font-size: 28px;
  margin-bottom: 20px;
}

.contact-desc {
  color: #909399;
  line-height: 1.8;
  margin-bottom: 30px;
}

.info-list {
  display: flex;
  flex-direction: column;
  gap: 24px;
}

.info-item {
  display: flex;
  gap: 16px;
  align-items: flex-start;
}

.info-icon {
  font-size: 32px;
  width: 48px;
  height: 48px;
  background-color: #f0f5ff;
  border-radius: 12px;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-shrink: 0;
}

.info-item h4 {
  font-size: 16px;
  margin-bottom: 4px;
  color: #303133;
}

.info-item p {
  font-size: 15px;
  font-weight: 500;
  color: #606266;
}

.info-item span {
  font-size: 13px;
  color: #909399;
}

.contact-form-wrapper {
  background-color: #f8fafc;
  padding: 40px;
  border-radius: 16px;
}

.form-row {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 20px;
}

.form-item {
  margin-bottom: 20px;
}

.form-item label {
  display: block;
  margin-bottom: 8px;
  font-size: 14px;
  font-weight: 500;
  color: #303133;
}

.form-item input,
.form-item select,
.form-item textarea {
  width: 100%;
  padding: 12px 16px;
  border: 1px solid #e4e7ed;
  border-radius: 8px;
  font-size: 14px;
  transition: all 0.3s;
  background-color: #fff;
  font-family: inherit;
}

.form-item input:focus,
.form-item select:focus,
.form-item textarea:focus {
  outline: none;
  border-color: #409eff;
  box-shadow: 0 0 0 3px rgba(64, 158, 255, 0.1);
}

.form-item textarea {
  resize: vertical;
}

.submit-btn {
  width: 100%;
  padding: 14px;
  font-size: 16px;
}

.map-section {
  padding: 40px 0 80px;
}

.map-placeholder {
  height: 400px;
  background-color: #f0f2f5;
  border-radius: 12px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 12px;
}

.map-placeholder span {
  font-size: 80px;
}

.map-placeholder p {
  color: #909399;
}

@media (max-width: 768px) {
  .contact-grid {
    grid-template-columns: 1fr;
  }

  .form-row {
    grid-template-columns: 1fr;
  }

  .page-banner h1 {
    font-size: 32px;
  }
}
</style>