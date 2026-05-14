# weihacking 站点迭代日志

> 仓库：`1596941391qq.github.io` | 周期：2026-05-10 ~ 05-13

---

## v1 — 修复 + 可读性 (05-10 ~ 05-12)

### Bug 修复

| Commit | 问题 | 修复 |
|--------|------|------|
| `c470ff4` | 周刊页 JS 崩溃导致内容不显示 | script.js 容错处理 |
| `fbabb92` | section{opacity:0} 依赖 IntersectionObserver | 7 个周刊页内联 opacity:1;transform:none |
| `2c12033` | 首页 #03 周刊标题只显示"从"字 | data-zh 属性内嵌 ASCII 引号改为「」 |
| `d459246` | tools.html 8 个 GitHub OG 图片加载失败 | 替换为内联 SVG 图标（语言色渐变 + 分类图标） |

### 内容去工程化

| Commit | 变更 |
|--------|------|
| `66ec3dc` | 移除首页 process-flow 三步交互流程（策略审计/内容部署/证据回写），删除"飞书表"工程细节对外暴露 |

### 可读性提升

| Commit | 变更 | 具体 |
|--------|------|------|
| `93a9dab` | CSS 字号放大 + 颜色加深 | body 16→17px, section p 16→17px, nl-article li 15→16px; --ink-s #3D3831→#2E2A24, --muted #8A8279→#6B665D |

### 内容分类重构

| Commit | 变更 |
|--------|------|
| `2ea16d5` | 首页知识产品区周刊/快讯/科普三栏分离。周刊卡片底部链接从"查看全部快讯"改为"浏览周刊存档"→knowledge.html。新增快讯入口卡片→hacking-news.html，科普入口卡片→geo-aeo-optimization-guide.html |

---

## v2 — CEO Review 驱动优化 (05-13)

### 问题修复

| Commit | 问题 | 修复 |
|--------|------|------|
| `1f6289a` | 首页 updates-band 前 5 条重复 | 移除重复条目，更新至 05-12/05-05 最新动态 |

### CEO Review 发现（已记录，待后续迭代）

| # | 发现 | 严重度 | 状态 |
|---|------|--------|------|
| 1 | 缺少 CTA 转化追踪（UTM 参数） | Critical | 待执行 |
| 2 | 45 个手工 HTML 文件无模板复用（SSG 迁移） | High | 中期规划 |
| 3 | 作为 SEO 从业者，个人站缺少 GEO 信号差异化 | High | 部分覆盖（周刊页已有 NewsArticle schema） |
| 4 | 首页推文哲思 section 内容量不足（仅 2 条） | Medium | 待补充 |
| 5 | og:image 大部分页面用默认 avatar.jpg | Medium | 待补全 |

---

## 技术债务

1. **SSG 迁移**：当前 45+ 手工 HTML 文件，无模板继承/组件复用。建议评估 Astro/11ty。
2. **JS 依赖**：section visibility 依赖 IntersectionObserver，周刊页已内联修复，其余 section 仍依赖 script.js。
3. **图片策略**：周刊页 header 图复用 newsletter-header-dark-tech.jpg，缺少每期独立封面。

---

## 文件变更统计

```
index.html          | 8 commits | 首页重构主战场
style.css           | 1 commit  | 全站字号+颜色
tools.html          | 1 commit  | SVG 图标替换
newsletter/*.html   | 2 commits | opacity 修复 + 生成脚本更新
scripts/nl-md2html.py | 1 commit | 模板 section 样式更新
```

---

## v3 — CEO Review 驱动：转化追踪 + SEO 信号 (05-13)

### 转化追踪（CEO Review Critical 项）

| Commit | 变更 | 具体 |
|--------|------|------|
| `2d47850` | 首页 CTA 添加 UTM 追踪 | 4 个飞书咨询链接分别加 utm_content=os1-banner/prod-high-authority/prod-social-interception/bottom-band |

### SEO 结构化数据

| Commit | 变更 |
|--------|------|
| `2d47850` | 4 个科普页补全 Article JSON-LD：geo-aeo-optimization-guide、pseo-agent-how-it-works、thinking、tools |

### 修复

| Commit | 变更 |
|--------|------|
| `2d47850` | issue-05 导航格式统一（与其他期一致） |

### CEO Review 状态更新

| # | 发现 | 严重度 | v3 状态 |
|---|------|--------|---------|
| 1 | CTA 转化追踪 | Critical | **已修复** — 全站 4 个 CTA 加 UTM |
| 2 | SSG 迁移 | High | 中期规划（本轮不执行） |
| 3 | GEO 信号 | High | **部分修复** — 4 个科普页加 Article schema |
| 4 | 推文内容不足 | Medium | 待补充 |
| 5 | og:image 统一 | Medium | 待补全 |

---

## v4 — 内容深化 + 社交分享优化 (05-13)

### 推文哲思补充（CEO Review Medium 项 #4）

| Commit | 变更 |
|--------|------|
| `5768f09` | 首页推文哲思 section 从 2 条补充至 4 条：新增「假环境淘汰论」(05-06) + 「SEO 终局是被引用」(05-11) |

### og:image 优化（CEO Review Medium 项 #5）

| Commit | 变更 |
|--------|------|
| `5768f09` | 首页 og:image 从 avatar.jpg 替换为 gsc-growth.jpg（GSC 增长截图，更能体现 SEO 专业度） |

### CEO Review 状态更新

| # | 发现 | 严重度 | v4 状态 |
|---|------|--------|---------|
| 1 | CTA 转化追踪 | Critical | **已修复** (v3) |
| 2 | SSG 迁移 | High | 中期规划（不执行） |
| 3 | GEO 信号 | High | **部分修复** (v3) |
| 4 | 推文内容不足 | Medium | **已修复** — 2→4 条 |
| 5 | og:image 统一 | Medium | **部分修复** — 首页已换，其余页面待统一 |

---

## v5 — 信任信号 + 内容结构化 (05-14)

### Updates-band 刷新

| Commit | 变更 |
|--------|------|
| `3520dea` | 首页动态栏更新至 05-14/05-13 最新变更，移除过旧条目（04-22/04-20） |

### 知识精选来源链接

| Commit | 变更 |
|--------|------|
| `3520dea` | 3 个 insight 卡片加来源超链接：Ahrefs 75K 品牌研究、Ahrefs 730K AI Mode 对比、Semrush 89K LinkedIn 研究 |

### 交付方法 section 结构化

| Commit | 变更 |
|--------|------|
| `3520dea` | 交付方法从纯文字段落升级为三阶段卡片（策略审计 → 内容部署 → 排名监控），每阶段标注具体产出物 |

### v5 新发现

| # | 发现 | 严重度 | 状态 |
|---|------|--------|------|
| 6 | 交付方法 section 无结构化内容 | Medium | **已修复** — 三阶段卡片 |
| 7 | 知识精选无来源链接，缺信任信号 | Medium | **已修复** — 3 个研究加超链接 |
| 8 | Updates-band 过时（最新 05-12） | Low | **已修复** — 更新至 05-14 |
