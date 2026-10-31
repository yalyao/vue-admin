<template>
  <footer class="site-footer">
    <div class="container footer-inner">
      <div class="footer-grid">
        <div class="footer-col">
          <div class="footer-brand">
            <span class="logo-icon">🚀</span>
            <span>科技有限公司</span>
          </div>
          <p class="footer-desc">
            专注于为企业提供数字化转型解决方案，用技术驱动商业增长。
          </p>
        </div>
        <div class="footer-col">
          <h4>快速导航</h4>
          <ul>
            <li><router-link to="/">首页</router-link></li>
            <li><router-link to="/about">关于我们</router-link></li>
            <li><router-link to="/services">产品服务</router-link></li>
            <li><router-link to="/news">新闻资讯</router-link></li>
            <li><router-link to="/contact">联系我们</router-link></li>
          </ul>
        </div>
        <div class="footer-col">
          <h4>联系方式</h4>
          <ul class="contact-list">
            <li>📞 400-888-8888</li>
            <li>📧 contact@company.com</li>
            <li>📍 北京市朝阳区科技园区</li>
            <li>🕐 周一至周五 9:00-18:00</li>
          </ul>
        </div>
        <div class="footer-col">
          <h4>关注我们</h4>
          <div class="social-icons">
            <span class="social-icon">微</span>
            <span class="social-icon">博</span>
            <span class="social-icon">抖</span>
            <span class="social-icon">知</span>
          </div>
          <p class="follow-tip">扫码关注公众号，获取最新动态</p>
        </div>
      </div>
    </div>
    <div class="footer-bottom">
      <div class="container">
        <p>© 2024 科技有限公司 版权所有 | 京ICP备12345678号</p>
      </div>
    </div>
  </footer>
</template>

<script setup>
</script>

<style scoped>
.site-footer {
  background-color: #1a1a2e;
  color: #a0aec0;
  padding-top: 60px;
}

.footer-inner {
  padding-bottom: 40px;
}

.footer-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 40px;
}

.footer-col h4 {
  color: #fff;
  font-size: 16px;
  margin-bottom: 20px;
  font-weight: 600;
}

.footer-brand {
  display: flex;
  align-items: center;
  gap: 8px;
  font-size: 20px;
  font-weight: 700;
  color: #fff;
  margin-bottom: 16px;
}

.logo-icon {
  font-size: 28px;
}

.footer-desc {
  font-size: 14px;
  line-height: 1.8;
}

.footer-col ul li {
  margin-bottom: 12px;
}

.footer-col ul li a {
  font-size: 14px;
  transition: color 0.3s;
}

.footer-col ul li a:hover {
  color: #409eff;
}

.contact-list li {
  font-size: 14px;
  margin-bottom: 12px;
}

.social-icons {
  display: flex;
  gap: 12px;
  margin-bottom: 16px;
}

.social-icon {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  background-color: rgba(255, 255, 255, 0.1);
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 14px;
  color: #fff;
  cursor: pointer;
  transition: all 0.3s;
}

.social-icon:hover {
  background-color: #409eff;
  transform: translateY(-3px);
}

.follow-tip {
  font-size: 13px;
  color: #718096;
}

.footer-bottom {
  border-top: 1px solid rgba(255, 255, 255, 0.1);
  padding: 20px 0;
}

.footer-bottom p {
  text-align: center;
  font-size: 13px;
  color: #718096;
}

@media (max-width: 768px) {
  .footer-grid {
    grid-template-columns: repeat(2, 1fr);
    gap: 30px;
  }
}

@media (max-width: 480px) {
  .footer-grid {
    grid-template-columns: 1fr;
  }
}
</style>