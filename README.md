# Hover Shapes · 图形悬停效果

使用 HTML 和 CSS 实现六个渐变图形，无需 JavaScript、外部依赖或构建工具。

## 功能

- 鼠标悬停时图形向上移动 10px。
- 阴影水平和垂直偏移均变为 0，保留 24px 模糊效果。
- 图形中央淡入显示 `hover`，鼠标离开时恢复原状。
- 支持 Tab 键聚焦，窄屏自动换行。

## 文件结构

```text
hover-shapes/
├── index.html       # 页面结构
├── css/
│   └── style.css    # 图形外观与悬停效果
├── README.md        # 项目说明
└── .gitignore       # 忽略系统临时文件
```

## 本地运行

保留文件夹结构，双击 `index.html`，使用浏览器打开。修改代码并保存后，刷新浏览器查看效果。

## 上传 GitHub

将本文件夹内的 `index.html`、`css` 文件夹、`README.md` 和 `.gitignore` 上传到自己的仓库根目录。保持 `css/style.css` 的相对路径不变。

本项目提供本地源代码，未创建远程仓库或发布网页。

## 代码入门

### HTML 结构

```html
<div class="tile" tabindex="0" aria-label="橙红色正方形">
  <div class="shape c1"><span>hover</span></div>
</div>
```

`tile` 是鼠标感应区域，`shape` 是图形，`c1` 设置第一个图形的颜色。`span` 放置文字。`tabindex="0"` 允许通过 Tab 键聚焦。

### 悬停移动

```css
.tile:hover .shape {
  transform: translateY(-10px);
}
```

鼠标放到 tile 上时，使内部 shape 向上移动 10px。负数向上，正数向下。外层保持原位，避免鼠标靠近下边缘时反复触发动画。

### 阴影

```css
box-shadow: 0 10px 24px var(--shadow);
```

依次表示水平偏移、垂直偏移、模糊半径和颜色。悬停时前两个数变成 `0 0`。`--shadow` 是各图形定义的颜色变量，`var(--shadow)` 读取它。

### 文字和过渡

`opacity: 0` 隐藏文字，`opacity: 1` 显示文字。`transition` 让变化在 0.3 秒内平滑完成。

## 常见修改

| 想修改什么 | 修改位置 |
| --- | --- |
| 图形大小 | `.tile` 的 `width`、`height` |
| 图形间距 | `.stage` 的 `gap` |
| 容器内部留白 | `.stage` 的 `padding` |
| 上移距离 | `translateY(-10px)` |
| 动画速度 | `transition` 中的 `0.3s` |
| 文字 | HTML 中的 `<span>hover</span>` |
| 圆角 | 各图形的 `border-radius` |
| 渐变颜色 | 各图形的 `--background` |

## 手动检查

将鼠标移入和移出每个图形，检查上移、阴影和文字变化；按 Tab 检查键盘效果；缩小窗口检查自动换行。
