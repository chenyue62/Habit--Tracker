# 🎯 习惯追踪器 - Habit Tracker

## 项目概述

习惯追踪器是一个基于纯前端技术开发的个人习惯管理应用，旨在帮助用户培养和维持良好的生活习惯。该项目采用现代化的Web设计理念，提供直观友好的用户界面和完整的数据管理功能。

## 🚀 在线演示

- **GitHub Pages**: [[https://yourusername.github.io/habit-tracker](https://yourusername.github.io/habit-tracker)](https://chenyue62.github.io/Habit--Tracker/)

## 📋 功能特性

### 核心功能
- **习惯创建管理**: 支持添加、删除自定义习惯
- **分类系统**: 内置6大分类（健康、学习、工作、生活、社交、娱乐）
- **每日打卡**: 一键标记习惯完成状态
- **进度追踪**: 实时显示完成率、连续天数等关键指标
- **可视化展示**: 21天日历网格直观显示完成情况

### 数据统计
- **总习惯数**: 当前创建的习惯总量
- **今日完成**: 当天已完成的习惯数量
- **最长连续**: 所有习惯中的最长连续完成天数
- **平均完成率**: 基于创建时间计算的整体完成率

### 用户体验
- **响应式设计**: 完美适配桌面端和移动端
- **现代化UI**: 渐变背景、毛玻璃效果、微动画
- **颜色个性化**: 6种预设颜色标识不同习惯
- **数据持久化**: 本地存储确保数据不丢失

## 🛠️ 技术栈

### 前端技术
- **HTML5**: 语义化标签，良好的结构设计
- **CSS3**: 
  - Flexbox + CSS Grid 响应式布局
  - CSS Variables 主题色彩管理
  - Transform + Transition 流畅动画效果
  - Backdrop-filter 毛玻璃背景效果
- **JavaScript ES6+**:
  - 类（Class）面向对象编程
  - 箭头函数、模板字符串等现代语法
  - DOM操作与事件处理
  - 日期时间计算算法

### 数据管理
- **LocalStorage**: 浏览器本地存储
- **JSON**: 数据序列化与反序列化
- **状态管理**: 自定义状态管理模式

### 开发工具
- **Git**: 版本控制
- **GitHub Pages**: 静态网站托管
- **VSCode**: 开发环境

## 🏗️ 架构设计

### 项目结构
```
habit-tracker/
├── index.html          # 单页面应用入口
├── README.md           # 项目说明文档
└── .gitignore         # Git忽略文件
```

### 代码架构
```javascript
class HabitTracker {
    constructor()       // 初始化应用状态
    init()             // 绑定事件监听器
    addHabit()         // 创建新习惯
    toggleHabit()      // 切换完成状态
    deleteHabit()      // 删除习惯
    getStreakDays()    // 计算连续天数
    getCompletionRate() // 计算完成率
    render()           // 渲染UI界面
    updateStats()      // 更新统计数据
    saveHabits()       // 保存到本地存储
    loadHabits()       // 从本地存储加载
}
```

## 💡 核心算法

### 连续天数计算
```javascript
getStreakDays(habit) {
    // 获取所有完成日期并按时间倒序排列
    const sortedDates = habit.completions
        .map(date => new Date(date))
        .sort((a, b) => b - a);
    
    let streak = 0;
    const today = new Date();
    
    // 从今天开始往前检查连续性
    for (let i = 0; i < sortedDates.length; i++) {
        const expectedDate = new Date(today);
        expectedDate.setDate(today.getDate() - streak);
        
        if (date.getTime() === expectedDate.getTime()) {
            streak++;
        } else {
            break; // 连续性中断
        }
    }
    return streak;
}
```

### 完成率计算
```javascript
getCompletionRate(habit) {
    const daysElapsed = Math.ceil(
        (new Date() - new Date(habit.createdAt)) / (1000 * 60 * 60 * 24)
    );
    return daysElapsed > 0 ? 
        Math.round((habit.completions.length / daysElapsed) * 100) : 0;
}
```

## 交互设计
- **即时反馈**: 按钮点击、悬停效果
- **状态指示**: 颜色变化表示不同状态
- **操作确认**: 删除操作提供二次确认
- **渐进增强**: 从基础功能到高级功能的层次设计

## 📱 响应式设计

### 断点设计
```css
/* 桌面端优先 */
.main-content {
    display: grid;
    grid-template-columns: 1fr 2fr;
}

/* 移动端适配 */
@media (max-width: 768px) {
    .main-content {
        grid-template-columns: 1fr;
    }
    .stats-grid {
        grid-template-columns: repeat(2, 1fr);
    }
}
```

### 适配策略
- **布局重排**: Grid布局自动适配不同屏幕尺寸
- **字体缩放**: 使用rem单位确保文字可读性
- **触摸优化**: 按钮大小满足移动端触摸需求

## 🔧 部署流程

### 1. 本地开发
```bash
# 创建项目目录
mkdir habit-tracker
cd habit-tracker

# 初始化Git仓库
git init

# 创建并编辑index.html
touch index.html
```

### 2. GitHub部署
```bash
# 添加文件到Git
git add .
git commit -m "Initial commit: Add habit tracker"

# 连接远程仓库
git remote add origin https://github.com/username/habit-tracker.git
git push -u origin main
```

### 3. 启用GitHub Pages
1. 进入GitHub仓库设置页面
2. 找到"Pages"选项
3. 选择"Deploy from a branch"
4. 选择"main"分支和"/ (root)"目录
5. 点击"Save"完成部署

## 📊 性能优化

### 加载性能
- **单文件架构**: 减少HTTP请求次数
- **内联样式**: CSS和JS内联，避免额外资源加载
- **轻量级**: 总文件大小<50KB，加载速度快

### 运行性能
- **事件委托**: 动态元素使用事件委托减少内存占用
- **局部更新**: 只更新变化的DOM元素
- **防抖节流**: 避免频繁的localStorage操作

### 数据性能
- **增量存储**: 仅存储必要的用户数据
- **数据压缩**: JSON格式高效存储
- **本地缓存**: 避免重复计算和网络请求

## 扩展方向

### 功能扩展
- [ ] **数据导出**: 支持CSV/JSON格式导出
- [ ] **主题切换**: 暗色模式支持
- [ ] **提醒功能**: 基于Notification API的提醒
- [ ] **统计图表**: 使用Chart.js添加趋势图
- [ ] **习惯模板**: 预设常见习惯模板

### 技术升级
- [ ] **PWA**: Progressive Web App离线支持
- [ ] **Vue/React**: 框架重构提升开发效率
- [ ] **TypeScript**: 类型安全和代码质量
- [ ] **云端同步**: 多设备数据同步

