<template>
  <div class="services-page fade-in">
    <section class="page-banner">
      <div class="container">
        <h1>产品服务</h1>
        <p>全方位的企业数字化解决方案</p>
      </div>
    </section>

    <section class="services-detail">
      <div class="container">
        <div class="service-detail-card" v-for="service in services" :key="service.id">
          <div class="service-info">
            <div class="service-emoji">{{ service.icon }}</div>
            <h2>{{ service.title }}</h2>
            <p>{{ service.desc }}</p>
            <ul class="service-features">
              <li v-for="feature in service.features" :key="feature">{{ feature }}</li>
            </ul>
            <router-link to="/contact" class="btn btn-primary">免费咨询</router-link>
          </div>
          <div class="service-image">
            <div class="image-placeholder">{{ service.image }}</div>
          </div>
        </div>
      </div>
    </section>

    <section class="process-section">
      <div class="container">
        <div class="section-title">
          <h2>服务流程</h2>
          <p>标准化的服务，让您放心无忧</p>
        </div>
        <div class="process-grid">
          <div class="process-card">
            <div class="process-step">1</div>
            <h3>需求沟通</h3>
            <p>深入了解您的业务需求和期望目标</p>
          </div>
          <div class="process-card">
            <div class="process-step">2</div>
            <h3>方案设计</h3>
            <p>提供专业的技术方案和报价</p>
          </div>
          <div class="process-card">
            <div class="process-step">3</div>
            <h3>开发实施</h3>
            <p>专业团队按期保质交付</p>
          </div>
          <div class="process-card">
            <div class="process-step">4</div>
            <h3>上线运维</h3>
            <p>长期技术支持和保障</p>
          </div>
        </div>
      </div>
    </section>

    <section class="faq-section">
      <div class="container">
        <div class="section-title">
          <h2>常见问题</h2>
          <p>您可能想了解的问题</p>
        </div>
        <div class="faq-list">
          <div class="faq-item" v-for="(faq, index) in faqs" :key="index" @click="toggleFaq(index)">
            <div class="faq-question">
              <span>{{ faq.q }}</span>
              <span class="faq-icon" :class="{ open: activeFaq === index }">+</span>
            </div>
            <div class="faq-answer" v-show="activeFaq === index">
              <p>{{ faq.a }}</p>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const activeFaq = ref(null)

const toggleFaq = (index) => {
  activeFaq.value = activeFaq.value === index ? null : index
}

const services = ref([
  {
    id: 1,
    icon: '💻',
    title: '网站建设',
    desc: '企业官网、电商平台、门户系统，专业设计定制开发，PC端和移动端完美适配。',
    features: ['响应式设计，手机电脑都能用', 'SEO优化，百度能搜到', 'CMS后台，自己能改内容', '1年免费技术支持'],
    image: '🌐'
  },
  {
    id: 2,
    icon: '📱',
    title: '小程序开发',
    desc: '微信小程序、支付宝小程序、抖音小程序，轻量化获客工具，助力业务增长。',
    features: ['原生小程序 + uni-app', '微信/支付宝/抖音多端', '企业认证指导', '数据分析埋点'],
    image: '📲'
  },
  {
    id: 3,
    icon: '📊',
    title: '数据中台',
    desc: '数据采集、存储、分析、可视化一站式解决方案，让数据真正驱动业务决策。',
    features: ['多源数据整合', '实时数据看板', 'AI智能分析', '自定义报表'],
    image: '📈'
  },
  {
    id: 4,
    icon: '🤖',
    title: 'AI应用',
    desc: '智能客服、内容生成、图像识别、语音交互，AI赋能业务全流程。',
    features: ['大模型接入', '智能客服系统', 'AI内容生成', '私有化部署'],
    image: '🧠'
  }
])

const faqs = ref([
  {
    q: '项目周期一般多久？',
    a: '简单的企业官网一般1-2周，小程序2-3周，数据中台等复杂项目1-3个月。具体时间需要根据需求评估。'
  },
  {
    q: '开发完成后有技术支持吗？',
    a: '有的，所有项目交付后提供1年免费技术支持，包括Bug修复和小功能调整。之后可以选择续费维护服务。'
  },
  {
    q: '你们负责域名和服务器吗？',
    a: '我们可以帮您选购域名和服务器，但费用由您承担。域名建议用您自己的身份注册，服务器推荐阿里云或腾讯云。'
  },
  {
    q: '后期可以自己改网站内容吗？',
    a: '可以的。我们提供带CMS后台的版本，您可以自己登录后台发布新闻、上传图片、修改产品信息等。'
  },
  {
    q: '价格是怎么算的？',
    a: '根据功能复杂度来定价。简单展示型网站3000-8000元，带CMS后台8000-15000元，更复杂的项目需要单独报价。'
  }
])
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

.services-detail {
  padding: 80px 0;
}

.service-detail-card {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 60px;
  align-items: center;
  padding: 40px;
  margin-bottom: 40px;
  background-color: #f8fafc;
  border-radius: 16px;
}

.service-detail-card:nth-child(even) {
  direction: rtl;
}

.service-detail-card:nth-child(even) > * {
  direction: ltr;
}

.service-emoji {
  font-size: 48px;
  margin-bottom: 16px;
}

.service-info h2 {
  font-size: 28px;
  margin-bottom: 16px;
}

.service-info > p {
  color: #606266;
  line-height: 1.8;
  margin-bottom: 20px;
}

.service-features li {
  padding: 8px 0;
  color: #606266;
  padding-left: 20px;
  position: relative;
}

.service-features li::before {
  content: '✓';
  position: absolute;
  left: 0;
  color: #409eff;
  font-weight: bold;
}

.image-placeholder {
  width: 100%;
  height: 300px;
  background: linear-gradient(135deg, #e0e7ff 0%, #c7d2fe 100%);
  border-radius: 12px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 100px;
}

.process-section {
  padding: 100px 0;
  background-color: #fff;
}

.process-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 30px;
}

.process-card {
  text-align: center;
  padding: 40px 20px;
  background-color: #f8fafc;
  border-radius: 12px;
}

.process-step {
  width: 60px;
  height: 60px;
  border-radius: 50%;
  background-color: #409eff;
  color: #fff;
  font-size: 24px;
  font-weight: 700;
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 0 auto 20px;
}

.process-card h3 {
  font-size: 18px;
  margin-bottom: 8px;
}

.process-card p {
  color: #909399;
  font-size: 14px;
}

.faq-section {
  padding: 100px 0;
  background-color: #f8fafc;
}

.faq-list {
  max-width: 800px;
  margin: 0 auto;
}

.faq-item {
  background-color: #fff;
  border-radius: 8px;
  margin-bottom: 16px;
  overflow: hidden;
  cursor: pointer;
}

.faq-question {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 20px 24px;
  font-weight: 500;
}

.faq-icon {
  font-size: 20px;
  color: #409eff;
  transition: transform 0.3s;
}

.faq-icon.open {
  transform: rotate(45deg);
}

.faq-answer {
  padding: 0 24px 20px;
}

.faq-answer p {
  color: #909399;
  line-height: 1.8;
}

@media (max-width: 768px) {
  .service-detail-card {
    grid-template-columns: 1fr;
    direction: ltr;
  }

  .service-detail-card:nth-child(even) {
    direction: ltr;
  }

  .process-grid {
    grid-template-columns: repeat(2, 1fr);
  }

  .page-banner h1 {
    font-size: 32px;
  }
}
</style>