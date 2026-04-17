# DESIGN.md - Web工具集

## 1. Visual Theme & Atmosphere
- **Mood**: 现代、简洁、高效、专业
- **Density**: 中等间距，信息清晰不拥挤
- **Philosophy**: 卡片式布局，每个工具独立入口，操作路径清晰

## 2. Color Palette & Roles
| Token | Hex | Usage |
|-------|-----|-------|
| `--primary` | `#667eea` | 主色、按钮、标题、链接 |
| `--primary-dark` | `#764ba2` | 渐变辅色、按钮渐变末端 |
| `--text-primary` | `#333` | 正文文字 |
| `--text-secondary` | `#666` | 描述文字、次要信息 |
| `--text-hint` | `#999` | 提示文字、辅助说明 |
| `--bg-light` | `#f8f9fa` | 卡片背景、分区背景 |
| `--border` | `#ddd` | 分割线、边框 |
| `--success` | `#28a745` | 成功标记、列表勾选 |
| `--danger` | `#ff4757` | 删除、错误 |
| `--white` | `#ffffff` | 卡片背景、容器 |

## 3. Typography Rules
| Level | Size | Weight | Color |
|-------|------|--------|-------|
| H1 (页面标题) | 2.5em / 3em | 300 | `#fff` (header) / `#333` |
| H2 (区块标题) | 2.2em | 300 | `#333` |
| H3 (卡片标题) | 1.4em / 1.5em | 500 | `#333` |
| Body | 1em / 14px | 400 | `#333` |
| Description | 0.9em / 1.1em | 400 | `#666` |
| Hint | 0.9em | 400 | `#999` |

字体族: `'Segoe UI', Tahoma, Geneva, Verdana, sans-serif`

## 4. Component Stylings

### 按钮
- 主按钮: `linear-gradient(135deg, #667eea, #764ba2)`，圆角8px，padding 12px 24px
- 次要按钮: `#6c757d` 背景，圆角8px
- Hover: `translateY(-2px)` + 阴影
- Disabled: `#ccc`，无transform

### 卡片
- 白色背景，圆角15px
- 阴影: `0 10px 30px rgba(0,0,0,0.1)`
- Hover: `translateY(-5px)`，阴影加深，边框变为 `#667eea`

### 上传区域
- 3px dashed `#ddd`，圆角10px
- Hover/拖入: 边框变 `#667eea`，背景 `#f0f4ff`

### 输入框
- 2px solid `#ddd`，圆角6px
- Focus: `border-color: #667eea`

## 5. Layout Principles
- **最大宽度**: 1200px（内容区），1000px（工具页）
- **间距**: padding 40px 内容区，卡片间距 30px
- **Grid**: `repeat(auto-fit, minmax(300px, 1fr))`
- **响应式**: ≤768px 时 padding 20px，grid 单列

## 6. Depth & Elevation
| Level | Shadow | Usage |
|-------|--------|-------|
| Card default | `0 10px 30px rgba(0,0,0,0.1)` | 卡片默认 |
| Card hover | `0 20px 40px rgba(0,0,0,0.15)` | 卡片悬浮 |
| Container | `0 20px 40px rgba(0,0,0,0.1)` | 主容器 |
| Preview | `0 2px 10px rgba(0,0,0,0.1)` | 预览区 |
| Loading overlay | `rgba(255,255,255,0.8)` 背景 | 加载遮罩 |

## 7. Do's and Don'ts
- **DO**: 使用渐变色 `#667eea` → `#764ba2` 作为主题色
- **DO**: 所有交互元素添加 hover/transition 效果
- **DO**: 工具页左上角保留返回主页按钮
- **DO**: 上传区域支持拖拽+点击两种方式
- **DON'T**: 使用 emoji 作为图标（卡片图标除外，用 Unicode 符号替代）
- **DON'T**: 引入新的颜色值，必须使用色板中的颜色
- **DON'T**: 卡片圆角使用其他值，统一 8px 或 15px

## 8. Responsive Behavior
- **Desktop (>768px)**: 多列 grid，完整 padding
- **Mobile (≤768px)**:
  - 标题字号缩小到 2.2em / 1.8em
  - Grid 变为单列
  - 内容区 padding 变为 20px
  - 按钮组 flex-wrap 换行

## 9. Agent Prompt Guide
生成新工具页面时：
1. 复用 `header` 结构（含返回按钮）
2. 使用相同的上传区域样式
3. 按钮使用 `.action-btn` 和 `.secondary-btn` 类
4. 工具卡片使用 grid 布局
5. 所有工具纯前端处理，不依赖后端
6. 页面底部保留 footer 和 GitHub 链接
