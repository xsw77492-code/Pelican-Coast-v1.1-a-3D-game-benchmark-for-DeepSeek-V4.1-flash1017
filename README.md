# Pelican Coast · 鹈鹕海岸

### 一个单文件 3D 游戏，也是一次对 DeepSeek-V4.1-flash1017 的端到端能力测试

> 只看画面，它是一个日落海岸上的鹈鹕骑行游戏。  
> 打开源码，它是一份 **232 KB、零依赖、零外部素材、经过真实浏览器测试** 的模型能力样本。

[简体中文](README.md) · [English](README.en.md) · [GitHub 仓库](https://github.com/xsw77492-code/Pelican-Coast-v1.1-a-3D-game-benchmark-for-DeepSeek-V4.1-flash1017)

<p align="center">
  <img alt="Model: DeepSeek-V4.1-flash1017" src="https://img.shields.io/badge/model-DeepSeek--V4.1--flash1017-4f6df5?style=flat-square">
  <img alt="Renderer: native WebGL2" src="https://img.shields.io/badge/renderer-native%20WebGL2-2f9e8f?style=flat-square">
  <img alt="Zero dependencies" src="https://img.shields.io/badge/dependencies-0-f0a45e?style=flat-square">
  <img alt="Single HTML file" src="https://img.shields.io/badge/build-single%20HTML-ef8f72?style=flat-square">
  <img alt="Version v1.1" src="https://img.shields.io/badge/version-v1.1-e98f72?style=flat-square">
  <img alt="License: MIT" src="https://img.shields.io/badge/license-MIT-f3a47c?style=flat-square">
</p>

![Pelican Coast 开始界面](screenshots/cover.jpg)

## 为什么做这个项目

2026 年 10 月，我们给 DeepSeek 新模型 **DeepSeek-V4.1-flash1017** 出了一道没有退路的题：

> “做一个鹈鹕骑车的 HTML 小游戏，可以是 3D 的，可以控制速度、躲避障碍物。  
> 动画界面一定要唯美，算法一定要准确。”

附加限制只有一条，但足够致命：

**不许使用 Three.js，不许使用游戏引擎，不许加载任何外部图片、音频或字体。所有东西放进一个 HTML 文件。**

我们想看的不是“模型能不能写出一段跑得起来的 demo”，而是它能不能把 **创意、3D 图形、碰撞数学、程序化美术、交互、音效、响应式 UI 和工程收尾** 一次做完。

结果就是这个项目：一只戴着草帽、围着丝巾的鹈鹕，骑着自行车穿过金色日落。

**Vibe-coded，但按工程标准收尾。**

> [!NOTE]
> 这是独立的模型能力测评作品，不是 DeepSeek 官方项目。模型名称按本次实验配置记录。

## 30 秒了解

| | |
| --- | --- |
| 交付形态 | 单个 `index.html`，约 **232 KB**，零运行依赖 |
| 渲染 | **原生 WebGL2**，自写矩阵/着色器/几何体/粒子系统 |
| 玩法 | 三车道速度跑酷 + 小鱼收集 + 连击 / 擦身 + 3 颗爱心 |
| 视觉 | 程序化日落海岸、鹈鹕骑手、动态丝巾、海面、棕榈、灯塔 |
| 平台 | 桌面键盘 + 手机触控，完全离线可玩 |
| 测试模型 | **DeepSeek-V4.1-flash1017**（本次实验配置） |
| 实测结果 | 60.2 FPS · 0 控制台错误 · 35 行障碍 0 公平性问题 · 移动端通过 |

## 开始玩

**本地运行（推荐）：** 下载仓库，双击 [`index.html`](index.html)。不需要安装、构建或联网。

或者启动一个静态服务器：

```bash
python -m http.server 8080
```

然后访问 <http://localhost:8080/>。

**GitHub Pages：** 推送到 GitHub 后，在 `Settings → Pages → Deploy from a branch` 选择 `main` 和 `/ (root)`，即可通过：

```text
https://xsw77492-code.github.io/Pelican-Coast-v1.1-a-3D-game-benchmark-for-DeepSeek-V4.1-flash1017/
```

开启 Pages 后即可在线游玩。

> [!TIP]
> 用 Chrome / Edge 打开效果最佳，需要支持 WebGL2。

## 操作

| 操作 | 键盘 |
| --- | --- |
| 加速 | `W` / `↑` |
| 减速、刹车 | `S` / `↓` / `Space` |
| 左右变道 | `A` `D` / `←` `→` |
| 暂停 / 继续 | `P` / `Esc` |
| 静音 | `M` |
| 结算后重新开始 | `R` / `Enter` |

触屏设备会自动显示左右变道、`slow` 和 `go` 按钮。

## 游戏画面

![游戏画面](screenshots/gameplay.jpg)

<p align="center">
  <img src="screenshots/near-miss.jpg" width="100%" alt="擦身而过与连击提示">
</p>

## 这版有什么

- **三车道速度跑酷**：躲开路障、木箱和路障锥，速度越快得分倍率越高。
- **擦身而过**：贴着障碍边缘通过，获得额外分数、连击、金色粒子、风声和专属提示。
- **连击 Combo**：小鱼和擦身都会积累连击；4.5 秒内没有续上会断连，碰撞立即清零。
- **连击倍率**：连击越高，全部得分越高，HUD 实时显示倍率；结算会记录最高连击。
- **3 颗爱心**：被撞后掉心、减速、短暂无敌；生命耗尽进入慢镜头和结算。
- **完整流程**：开场、倒计时、游戏、暂停、死亡、结算、重开、本地最佳成绩。
- **唯美海岸**：动态海面、晚霞、棕榈、灯塔、帆船、飞鸟、浮游粒子。
- **重新制作的鹈鹕**：更长的 S 形颈部、羽毛领、收拢的翼羽、扇形尾羽、宽檐草帽与花饰、飘动丝巾、后座花束。
- **移动端适配**：桌面和手机共用同一个文件，触控按钮自动出现。

## 为什么这是一个有难度的模型测试

这个题目真正难的地方，不是“画一只鹈鹕”。

- **零依赖**：不能靠 Three.js、游戏引擎或现成示例蒙混过关。
- **3D 数学**：相机、投影、光照、法线、矩阵、扫掠碰撞，全部要自己实现。
- **程序化美术**：海岸、云、海面、鹈鹕、自行车、帽子、围巾、花，全部由代码生成。
- **算法正确性**：不能出现“看起来能躲，实际无路可走”的死局。
- **状态完整**：开场、倒计时、暂停、掉心、死亡、结算、重开、本地存储，一个都不能漏。
- **性能与响应式**：既要 60 FPS，也要 375px 宽的手机能玩。
- **审美**：这往往是最难测试的部分——模型需要做出一致的色彩、构图和角色气质。

更关键的是：**它必须真的能运行**，而不是只生成一篇看起来像游戏的代码。

## 模型评测结果

完整记录见 [EVALUATION.md](EVALUATION.md)。

| 项目 | 结果 |
| --- | --- |
| 交付 | 单文件、零运行依赖、零外部素材 |
| 首帧时间 | 约 0.9 秒 |
| 游戏帧率 @ 1440×900 | **60.2 FPS** |
| 控制台错误 | **0** |
| WebGL 错误码 | **0** |
| 连续障碍公平性 | **35 行，0 处不可达** |
| 擦身判定 / 加分 / 特效 | 通过 |
| 连击累积 / 4.5 秒断连 / 碰撞断连 | 通过 |
| 最高连击进入结算 | 通过 |
| 碰撞掉心 → 死亡 → 结算 | 通过 |
| 暂停 / 恢复 / 重开 | 通过 |
| 最佳成绩 localStorage | 通过 |
| 移动端 390 / 375 宽度 | 通过，无横向溢出 |
| 移动端触控换道 | 通过 |

测试环境：

```text
Chrome + WebGL2
ANGLE / Direct3D 11
Intel UHD Graphics
1440 × 900 / 60.2 FPS
```

## v1.0 → v1.1：不是一次生成就结束

这个项目经历了两个阶段：

- **v1.0**：从零完成场景、角色、玩法、UI、音效和移动端适配。
- **v1.1**：根据真实试玩反馈，加入连击 / 擦身，重新制作鹈鹕模型，并补上完整的浏览器回归测试。

这也是它适合作为模型评测样本的原因：它不仅看“第一次生成得多好”，也看模型能不能在后续反馈中继续修改、保持正确性，并把体验做完整。

## 技术细节

<details>
<summary><strong>展开查看引擎与算法</strong></summary>

- **自写 WebGL2 渲染器**：没有 Three.js，自行实现矩阵、透视投影、网格构建、着色器和帧循环。
- **程序化几何**：鹈鹕、自行车、障碍、棕榈、灯塔、海岸线、鱼群都在启动时生成。
- **动态丝巾**：每帧更新自定义布料网格，随速度、转向和时间形成不同的飘动曲线。
- **固定 120 Hz 模拟**：渲染和玩法解耦，低帧率下不会因为步长变大而穿模。
- **连续碰撞检测**：每一步用障碍扫过的 Z 区间与骑手碰撞盒求交，薄障碍也不会被跨过。
- **公平障碍生成**：每行最多堵塞两条车道；上一行的所有安全车道，必须能在一次变道内到达下一行的安全车道。
- **WebAudio 合成音效**：海浪、风声、拾取、碰撞、擦身、连击、倒计时、结算音全部实时合成。
- **响应式渲染**：小屏幕限制像素比，移动端有独立触控层。
- **本地持久化**：最高分与静音偏好保存在浏览器 `localStorage`。

</details>

## 用新模型复现这个测试

如果你想用另一个模型重新生成一份，或者对比不同版本：

1. 给它同样的限制：**单文件、零依赖、零外部素材、完整可玩、动画唯美、碰撞和障碍生成准确**。
2. 要求它先给方案，再实现。
3. 用真实浏览器打开，而不是只看代码。
4. 检查障碍是否可能出现无路可走的死局。
5. 检查高低帧率下的碰撞、暂停、死亡、重开和移动端。
6. 把结果记录在 [EVALUATION.md](EVALUATION.md)，欢迎提交 PR。

### 自动化调试接口

页面暴露了一个用于测试的对象 `window.__pelicanCoast`：

```js
window.__pelicanCoast.getState();          // 当前状态、连击、公平性日志
window.__pelicanCoast.start();             // 开始游戏
window.__pelicanCoast.skipCountdown();     // 跳过倒计时
window.__pelicanCoast.advance(5);          // 快进 5 秒玩法
window.__pelicanCoast.setSpeed(24);        // 设置速度
window.__pelicanCoast.setInvincible(999);  // 测试 / 演示用
window.__pelicanCoast.moveLane(1);         // 左 / 右变道目标
window.__pelicanCoast.stageNearMiss();     // 构造一次可控的擦身测试
window.__pelicanCoast.pause();
window.__pelicanCoast.resume();
```

它不属于稳定的公开 API，仅用于自动化截图和玩法验证。

## 路线图

- **v1.2**：每日种子挑战、更多障碍类型、60 秒冲刺模式
- **v1.3**：可解锁的车漆、帽子、围巾配色
- **以后**：幽灵回放、更多海岸场景、潜在的多模型对比报告

## 贡献

欢迎：

- 提交你测试的新模型结果
- 改进玩法、视觉或性能
- 报告 bug 或提出更优雅的实现方式
- 把这个项目作为单文件游戏 / 模型评测的参考

如果你要提交 PR，请尽量保持 **单文件、零外部依赖、离线可玩**。

## License

[MIT](LICENSE) © 2026 xu-shiwei66

---

### ⭐ 如果这个项目对你有用

如果你也在评测代码模型、做单文件游戏，或者只是喜欢这只骑车的鹈鹕，**点一个 Star** 会让更多做模型评测的人看到这个样本。

**Tested with DeepSeek-V4.1-flash1017 · Built in DeepSeek Harness · Independent project, not affiliated with DeepSeek.**
