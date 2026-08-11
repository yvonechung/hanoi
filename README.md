# 汉诺塔 · Tower of Hanoi（手机版）

一款纯前端、零依赖的汉诺塔手机小游戏。单个 `index.html` 文件即可运行，支持触屏拖拽与点击操作，离线可用，可直接部署到 GitHub Pages。

![游戏截图](screenshot.png)

## 玩法

> 目标是把左侧第一根柱子上的所有圆盘，按**大盘在下、小盘在上**的规则，全部移到最右侧的柱子。

- **移动规则**：每次只能移动一根圆盘，且只能放到空柱或比它大的圆盘之上。
- **操作方式**
  - 手机：直接**拖拽**顶部圆盘到目标柱子；或先点一下选中圆盘、再点目标柱子。
  - 桌面：用鼠标拖拽或点击同样可用。
- **通关**：把所有圆盘都移到最右侧柱子即胜利。

## 功能特性

| 特性 | 说明 |
| --- | --- |
| 难度选择 | 3 / 4 / 5 / 6 / 7 / 8 盘，一键切换 |
| 双操作 | 触屏拖拽 + 点选移动，鼠标同样支持 |
| 步数 & 计时 | 实时统计，胜利时展示总步数、用时与理论最优步数 |
| 撤销 | 支持逐步回退 |
| 提示 | 基于 BFS 求解当前局面的最优下一步，即使走错也能回到最优路径 |
| 星级评价 | 3 星（达到理论最优）、2 星（≤1.5 倍最优）、1 星 |
| 最佳记录 | 用 `localStorage` 保存每关最少步数（隐私模式下自动降级） |
| 移动端适配 | 竖屏布局、安全区适配、禁用双指缩放与误触滚动 |
| 胜利弹窗 | 展示成绩、星级与「新纪录」标识，可「下一关 / 再玩一次」 |

## 本地运行

无需任何构建步骤，任选一种方式：

1. **直接打开**：双击 `index.html` 用浏览器打开即可。
2. **本地服务器**（可选）：
   ```bash
   # 使用 Python
   python3 -m http.server 8000
   # 然后访问 http://localhost:8000
   ```

## 部署到 GitHub Pages

1. 在 GitHub 新建一个仓库（例如 `hanoi`）。
2. 将本仓库内容推送上去：
   ```bash
   git init
   git add .
   git commit -m "Add Tower of Hanoi mobile game"
   git branch -M main
   git remote add origin https://github.com/你的用户名/hanoi.git
   git push -u origin main
   ```
3. 在仓库 **Settings → Pages** 中，Source 选择 `main` 分支、`/ (root)`，保存后即可通过
   `https://你的用户名.github.io/hanoi/` 访问。

## 技术说明

- 纯原生 HTML + CSS + Canvas + JavaScript，**无任何第三方依赖**。
- 渲染基于 `<canvas>`，按 `devicePixelRatio` 做高清适配。
- 提示功能使用 **BFS** 从当前局面搜索最短路径，保证给出的是真正的最优下一步。
- 全部逻辑在单文件内，方便嵌入任意静态站点或打包成 PWA / WebView。

## 文件结构

```
.
├── index.html      # 游戏本体（单文件，包含全部 HTML/CSS/JS）
├── screenshot.png  # 游戏截图（用于 README）
├── LICENSE         # MIT 许可证
└── README.md       # 本文件
```

## License

[MIT](LICENSE) © 2026
