<script setup>
import { ref } from 'vue'
import { Message, Refresh, Setting, Box, Link, More, Monitor, ChatDotRound, User, Collection, Document, Promotion } from '@element-plus/icons-vue'
import { useRouter } from 'vue-router'

const messageInput = ref('')
const hotTopics = ref([
  {
    icon: '🔥',
    title: 'Kimi k1 视觉思考模型抢先体验',
    type: 'hot'
  },
  {
    icon: '🤖',
    title: '了解人工智能的必读书单',
    type: 'ai'
  },
  {
    icon: '🌐',
    title: '谷歌回应美司法部"强制出售Chrome"计划',
    type: 'news'
  },
  {
    icon: '📚',
    title: '本田与日产将率先采用特斯拉充电标准',
    type: 'news'
  }
])

const router = useRouter()

const goHome = () => {
  router.push('/')
}
</script>

<template>
  <div class="home-container">
    <div class="sidebar-container">
      <div class="sidebar">
        <el-menu
          class="sidebar-menu"
          default-active="1"
          :collapse="true">
          <div class="menu-header" @click="goHome" title="回到首页">
            <img src="@/assets/logo.svg" alt="KIMI" class="menu-logo"/>
            <div class="logo-tooltip">回到首页</div>
          </div>
          <div class="menu-items menu-items-main">
            <el-menu-item index="1" title="对话">
              <el-icon><ChatDotRound /></el-icon>
            </el-menu-item>
            <el-menu-item index="2" title="收藏">
              <el-icon><Collection /></el-icon>
            </el-menu-item>
            <el-menu-item index="3" title="历史">
              <el-icon><Refresh /></el-icon>
            </el-menu-item>
            <el-menu-item index="4" title="文档">
              <el-icon><Document /></el-icon>
            </el-menu-item>
          </div>
          <div class="menu-items menu-items-bottom">
            <el-menu-item index="5" title="公告">
              <el-icon><Promotion /></el-icon>
            </el-menu-item>
            <el-menu-item index="6" title="设置">
              <el-icon><Setting /></el-icon>
            </el-menu-item>
            <el-menu-item index="7" title="个人">
              <el-icon><User /></el-icon>
            </el-menu-item>
          </div>
        </el-menu>
      </div>
    </div>

    <!-- 主要内容区域 -->
    <div class="main-content">
      <!-- 顶部区域 -->
      <div class="top-bar">
        <div class="logo">
          <img src="@/assets/logo.svg" alt="KIMI" />
          <span class="slogan">登录一下 和 Kimi 一起玩月</span>
        </div>
        <div class="action-buttons">
          <el-button-group>
            <el-button :icon="Box" size="large">导入</el-button>
            <el-button :icon="Link" size="large">链接</el-button>
            <el-button :icon="More" size="large">更多</el-button>
          </el-button-group>
        </div>
      </div>

      <!-- 对话内容区域 -->
      <div class="chat-container">
        <div class="welcome-section">
          <h2>欢迎使用 KIMI</h2>
          <p>你的智能助手，随时为你解答问题</p>
        </div>

        <div class="hot-topics">
          <h3>热门问题</h3>
          <div class="topic-grid">
            <div v-for="(topic, index) in hotTopics" 
                 :key="index" 
                 class="topic-card">
              <span class="topic-icon">{{ topic.icon }}</span>
              <span class="topic-title">{{ topic.title }}</span>
            </div>
          </div>
        </div>

        <!-- 底部输入区域 -->
        <div class="input-area">
          <el-input
            v-model="messageInput"
            type="textarea"
            :rows="3"
            placeholder="尽情输入问题..."
            resize="none"
          />
          <div class="input-actions">
            <el-button type="primary" round size="large">发送</el-button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
/* 容器布局 */
.home-container {
  display: flex;
  height: 100vh;
  background-color: #f5f7fa;
  position: relative;
}

/* 侧边栏样式 */
.sidebar-container {
  position: fixed;
  left: 28px;
  top: 50%;
  transform: translateY(-50%);
  z-index: 10;
  padding: 5px;
}

.sidebar {
  width: 56px;
  background-color: rgba(255, 255, 255, 0.98);
  border-radius: 24px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.02),
              0 4px 12px rgba(0, 0, 0, 0.02);
  overflow: visible;
  padding: 0;
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  position: relative;
  display: flex;
  flex-direction: column;
  height: auto;
  min-height: 440px;
}

.sidebar:hover {
  transform: scale(1.02);
  box-shadow: 0 6px 16px rgba(0, 0, 0, 0.04),
              0 8px 24px rgba(0, 0, 0, 0.02),
              0 12px 32px rgba(0, 0, 0, 0.01);
}

/* 菜单头部样式 */
.menu-header {
  height: 64px;
  width: 56px;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: 0;
  position: relative;
  background: linear-gradient(
    to bottom,
    rgba(255, 255, 255, 1),
    rgba(255, 255, 255, 0.98)
  );
  border-radius: 24px 24px 0 0;
  padding: 16px 0;
  cursor: pointer;
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
}

.menu-logo {
  width: 28px;
  height: 28px;
  transition: transform 0.3s ease;
}

.menu-header:hover .menu-logo {
  transform: scale(1.1);
}

/* 菜单项容器 */
.menu-items {
  display: flex;
  flex-direction: column;
  gap: 4px;
  padding: 8px 6px;
}

.menu-items-main {
  padding-top: 4px;
  display: flex;
  flex-direction: column;
  gap: 8px;
}

.menu-items-bottom {
  margin-top: auto;
  padding-top: 12px;
  padding-bottom: 8px;
  border-top: 1px solid rgba(0, 0, 0, 0.06);
  display: flex;
  flex-direction: column;
  gap: 8px;
}

/* 菜单基础样式 */
.sidebar-menu {
  border: none;
  background: transparent;
  height: 100%;
  display: flex;
  flex-direction: column;
}

/* 菜单项样式 */
.sidebar-menu :deep(.el-menu-item) {
  height: 44px;
  min-height: 44px;
  line-height: 44px;
  text-align: center;
  padding: 0 !important;
  margin: 0;
  border-radius: 22px;
  transition: all 0.3s cubic-bezier(0.34, 1.56, 0.64, 1);
  position: relative;
  overflow: visible;
  background: transparent;
}

.sidebar-menu :deep(.el-menu-item .el-icon) {
  margin: 0;
  font-size: 24px;
  width: 44px;
  height: 44px;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: all 0.3s cubic-bezier(0.34, 1.56, 0.64, 1);
  color: #606266;
}

/* 悬浮提示样式 */
.sidebar-menu :deep(.el-menu-item)::after {
  content: attr(title);
  position: absolute;
  left: 140%;
  top: 50%;
  transform: translateY(-50%) scale(0.9);
  background: rgba(0, 0, 0, 0.85);
  color: white;
  padding: 6px 12px;
  border-radius: 6px;
  font-size: 13px;
  opacity: 0;
  visibility: hidden;
  transition: all 0.3s cubic-bezier(0.34, 1.56, 0.64, 1);
  pointer-events: none;
  white-space: nowrap;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  border: 1px solid rgba(255, 255, 255, 0.1);
  z-index: 100;
}

.sidebar-menu :deep(.el-menu-item:hover)::after {
  opacity: 1;
  visibility: visible;
  transform: translateY(-50%) scale(1);
}

/* 激活和悬浮状态 */
.sidebar-menu :deep(.el-menu-item.is-active) {
  background: transparent;
}

.sidebar-menu :deep(.el-menu-item.is-active .el-icon) {
  color: #409EFF;
  transform: scale(1.1);
}

.sidebar-menu :deep(.el-menu-item:hover) {
  background: transparent;
}

.sidebar-menu :deep(.el-menu-item:hover .el-icon) {
  transform: scale(1.2);
  color: #409EFF;
}

/* 点击效果 */
.sidebar-menu :deep(.el-menu-item:active .el-icon) {
  transform: scale(0.95);
}

/* 主内容区域 */
.main-content {
  flex: 1;
  margin-left: 100px;
  display: flex;
  flex-direction: column;
  overflow: hidden;
}

/* 顶部栏样式 */
.top-bar {
  padding: 16px 24px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: #fff;
  border-bottom: 1px solid #e4e7ed;
}

.logo {
  display: flex;
  align-items: center;
  gap: 16px;
}

.logo img {
  height: 40px;
}

.slogan {
  color: #606266;
  font-size: 16px;
}

/* 聊天容器样式 */
.chat-container {
  flex: 1;
  display: flex;
  flex-direction: column;
  padding: 40px;
  overflow: hidden;
}

/* 欢迎区域样式 */
.welcome-section {
  text-align: center;
  margin-bottom: 40px;
}

.welcome-section h2 {
  font-size: 32px;
  color: #303133;
  margin-bottom: 12px;
}

.welcome-section p {
  font-size: 16px;
  color: #606266;
}

/* 热门话题样式 */
.hot-topics {
  margin-bottom: 40px;
}

.hot-topics h3 {
  font-size: 18px;
  color: #303133;
  margin-bottom: 20px;
}

.topic-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
  gap: 16px;
}

.topic-card {
  background: #fff;
  padding: 16px;
  border-radius: 8px;
  display: flex;
  align-items: center;
  gap: 12px;
  cursor: pointer;
  transition: all 0.3s;
  box-shadow: 0 2px 12px rgba(0, 0, 0, 0.05);
}

.topic-card:hover {
  transform: translateY(-2px);
  box-shadow: 0 4px 16px rgba(0, 0, 0, 0.1);
}

.topic-icon {
  font-size: 24px;
}

.topic-title {
  font-size: 14px;
  color: #303133;
}

/* 输入区域样式 */
.input-area {
  margin-top: auto;
  padding: 24px;
  background-color: #fff;
  border-radius: 12px;
  box-shadow: 0 -2px 12px rgba(0, 0, 0, 0.1);
}

.input-actions {
  display: flex;
  justify-content: flex-end;
  margin-top: 16px;
}

.el-button {
  padding: 12px 24px;
}

:deep(.el-textarea__inner) {
  border-radius: 8px;
  padding: 12px;
  font-size: 16px;
}

/* 调整菜单项容器样式 */
.menu-items {
  display: flex;
  flex-direction: column;
  gap: 6px;
  padding: 0 6px;
}

/* 主要功能区样式 */
.menu-items-main {
  padding-top: 8px;
  display: flex;
  flex-direction: column;
  gap: 8px;
}

/* 底部功能区样式 */
.menu-items-bottom {
  margin-top: auto;
  padding-top: 12px;
  padding-bottom: 8px;
  border-top: 1px solid rgba(0, 0, 0, 0.06);
  display: flex;
  flex-direction: column;
  gap: 8px;
}

/* 调整菜单项样式 */
.sidebar-menu :deep(.el-menu-item) {
  height: 44px;
  min-height: 44px;
  line-height: 44px;
  text-align: center;
  padding: 0 !important;
  margin: 0;
  border-radius: 22px;
}

.sidebar-menu :deep(.el-menu-item .el-icon) {
  margin: 0;
  font-size: 24px;
  width: 44px;
  height: 44px;
  display: flex;
  align-items: center;
  justify-content: center;
}

/* 调整悬浮提示样式 */
.sidebar-menu :deep(.el-menu-item)::after {
  left: 140%;
  font-size: 13px;
  padding: 6px 12px;
  border-radius: 6px;
  background: rgba(0, 0, 0, 0.8);
}

/* 优化分组间距 */
.menu-items + .menu-items {
  margin-top: 8px;
}

/* 添加分割线样式 */
.menu-header::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 8px;
  right: 8px;
  height: 1px;
  background: rgba(0, 0, 0, 0.04);
}

/* Logo提示框样式 */
.logo-tooltip {
  position: absolute;
  left: 140%;
  top: 50%;
  transform: translateY(-50%) scale(0.9);
  background: rgba(0, 0, 0, 0.85);
  color: white;
  padding: 6px 12px;
  border-radius: 6px;
  font-size: 13px;
  opacity: 0;
  visibility: hidden;
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  pointer-events: none;
  white-space: nowrap;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  border: 1px solid rgba(255, 255, 255, 0.1);
  z-index: 100;
}

/* Logo提示框显示效果 */
.menu-header:hover .logo-tooltip {
  opacity: 1;
  visibility: visible;
  transform: translateY(-50%) scale(1);
}

/* 点击效果 */
.menu-header:active {
  transform: scale(0.95);
}

.menu-header:active .menu-logo {
  transform: scale(0.95);
}

/* 调整菜单项悬浮和激活状态 */
.sidebar-menu :deep(.el-menu-item) {
  height: 44px;
  min-height: 44px;
  line-height: 44px;
  text-align: center;
  padding: 0 !important;
  margin: 0;
  border-radius: 22px;
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  position: relative;
  overflow: visible;
  background: transparent;
}

/* 图标基础样式 */
.sidebar-menu :deep(.el-menu-item .el-icon) {
  margin: 0;
  font-size: 24px;
  width: 44px;
  height: 44px;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  color: #606266;
}

/* 移除菜单项悬浮背景 */
.sidebar-menu :deep(.el-menu-item:hover) {
  background: transparent;
}

/* 优化图标悬浮效果 */
.sidebar-menu :deep(.el-menu-item:hover .el-icon) {
  transform: scale(1.2);
  color: #409EFF;
}

/* 优化激活状态 */
.sidebar-menu :deep(.el-menu-item.is-active) {
  background: transparent;
}

.sidebar-menu :deep(.el-menu-item.is-active .el-icon) {
  color: #409EFF;
  transform: scale(1.1);
  filter: drop-shadow(0 0 4px rgba(64, 158, 255, 0.2));
}

/* 点击效果 */
.sidebar-menu :deep(.el-menu-item:active .el-icon) {
  transform: scale(0.95);
}

/* 优化过渡效果 */
.sidebar-menu :deep(.el-menu-item),
.sidebar-menu :deep(.el-menu-item .el-icon) {
  transition: all 0.3s cubic-bezier(0.34, 1.56, 0.64, 1);
}

/* 移除之前的渐变和阴影效果 */
.sidebar-menu :deep(.el-menu-item)::before {
  display: none;
}

/* 调整提示框动画 */
.sidebar-menu :deep(.el-menu-item)::after {
  transition: all 0.3s cubic-bezier(0.34, 1.56, 0.64, 1);
}
</style>
