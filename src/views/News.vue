<template>
  <div class="news-page fade-in">
    <section class="page-banner">
      <div class="container">
        <h1>新闻资讯</h1>
        <p>了解我们的最新动态和行业洞察</p>
      </div>
    </section>

    <section class="news-section">
      <div class="container">
        <div class="news-grid">
          <div class="news-card" v-for="item in newsList" :key="item.id">
            <div class="news-image">{{ item.emoji }}</div>
            <div class="news-content">
              <div class="news-meta">
                <span class="news-category">{{ item.category }}</span>
                <span class="news-date">{{ item.date }}</span>
              </div>
              <h3>{{ item.title }}</h3>
              <p>{{ item.summary }}</p>
              <span class="news-link">阅读全文 →</span>
            </div>
          </div>
        </div>

        <div class="pagination">
          <span class="page-btn disabled">‹</span>
          <span class="page-btn active">1</span>
          <span class="page-btn">2</span>
          <span class="page-btn">3</span>
          <span class="page-btn">›</span>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const newsList = ref([
  {
    id: 1,
    emoji: '🏆',
    title: '公司荣获2023年度最佳技术服务商',
    summary: '我们凭借卓越的技术实力和优质的客户服务，荣获行业权威奖项，这是对我们十年努力的最好肯定。',
    category: '公司动态',
    date: '2024-01-15'
  },
  {
    id: 2,
    emoji: '🚀',
    title: '新产品发布：智能数据分析平台2.0',
    summary: '全新升级的数据平台，更强大的分析能力，更直观的数据可视化，助力企业数据驱动决策。',
    category: '产品更新',
    date: '2024-01-10'
  },
  {
    id: 3,
    emoji: '💡',
    title: 'AI如何改变中小企业的运营模式',
    summary: '从智能客服到自动化营销，AI正在重塑企业的每一个运营环节，我们来详细分析。',
    category: '行业洞察',
    date: '2024-01-05'
  },
  {
    id: 4,
    emoji: '📰',
    title: '2024年企业数字化转型趋势预测',
    summary: '新的一年，企业数字化将呈现哪些新趋势？我们结合行业经验给出专业预测。',
    category: '行业洞察',
    date: '2024-01-02'
  },
  {
    id: 5,
    emoji: '🎉',
    title: '热烈庆祝公司成立十周年',
    summary: '十年风雨兼程，感谢每一位客户的信任与支持，未来我们继续前行！',
    category: '公司动态',
    date: '2023-12-28'
  },
  {
    id: 6,
    emoji: '🔧',
    title: '企业官网维护的5个关键要点',
    summary: '很多企业做了网站就不管了，这5个维护要点直接影响网站效果，快来看看。',
    category: '技术分享',
    date: '2023-12-20'
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

.news-section {
  padding: 80px 0;
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
  cursor: pointer;
}

.news-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 15px 30px rgba(0, 0, 0, 0.08);
}

.news-image {
  height: 200px;
  background: linear-gradient(135deg, #f5f7fa 0%, #e4e7ed 100%);
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 64px;
}

.news-content {
  padding: 24px;
}

.news-meta {
  display: flex;
  gap: 12px;
  margin-bottom: 12px;
}

.news-category {
  padding: 2px 10px;
  background-color: #ecf5ff;
  color: #409eff;
  font-size: 12px;
  border-radius: 4px;
}

.news-date {
  font-size: 13px;
  color: #909399;
}

.news-content h3 {
  font-size: 18px;
  margin-bottom: 10px;
  color: #303133;
  line-height: 1.5;
}

.news-content h3:hover {
  color: #409eff;
}

.news-content p {
  color: #909399;
  font-size: 14px;
  margin-bottom: 16px;
  line-height: 1.6;
}

.news-link {
  color: #409eff;
  font-size: 14px;
  font-weight: 500;
}

.pagination {
  display: flex;
  justify-content: center;
  gap: 8px;
  margin-top: 50px;
}

.page-btn {
  width: 40px;
  height: 40px;
  border-radius: 6px;
  display: flex;
  align-items: center;
  justify-content: center;
  background-color: #fff;
  border: 1px solid #e4e7ed;
  color: #606266;
  cursor: pointer;
  transition: all 0.3s;
}

.page-btn:hover:not(.disabled):not(.active) {
  border-color: #409eff;
  color: #409eff;
}

.page-btn.active {
  background-color: #409eff;
  border-color: #409eff;
  color: #fff;
}

.page-btn.disabled {
  color: #c0c4cc;
  cursor: not-allowed;
}

@media (max-width: 768px) {
  .news-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (max-width: 480px) {
  .news-grid {
    grid-template-columns: 1fr;
  }
}
</style>