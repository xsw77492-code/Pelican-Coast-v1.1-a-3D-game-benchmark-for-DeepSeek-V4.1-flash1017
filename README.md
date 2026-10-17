# Pelican Coast · 鹈鹕海岸

> 一部单文件、离线可玩的低多边形 3D 海岸骑行小游戏。  
> A single-file, offline 3D pelican cycling game built with native WebGL2 — no runtime libraries, no external assets.

这是一个用来测试、展示和对比代码生成模型的小项目。它从空旷的 HTML 开始，最终成为一个无需构建、无需联网、用浏览器直接打开就能玩的完整小游戏。

![Pelican Coast 开始界面](screenshots/cover.jpg)

## 游戏

沿着日落海岸线一直骑下去。

- 三车道自动前进，控制速度与换道，躲开路障、木箱和路障锥
- 收集小鱼获得额外分数，速度越快得分倍率越高
- 3 颗爱心；被撞后掉心、减速并短暂无敌
- 结算显示距离、得分、小鱼与历史最佳；最佳成绩保存在浏览器本地
- 暂停、静音、重开；手机和平板会有触屏按钮

![Pelican Coast 游戏画面](screenshots/gameplay.jpg)

## 操作

| 操作 | 键盘 |
| --- | --- |
| 加速 | `W` / `↑` |
| 减速、刹车 | `S` / `↓` / `Space` |
| 左右变道 | `A` `D` / `←` `→` |
| 暂停 / 继续 | `P` / `Esc` |
| 静音 | `M` |
| 结算后重新开始 | `R` / `Enter` |

触屏设备会自动显示左右变道、slow 和 go 按钮。

## 设计和技术

- **原生 WebGL2，单文件**：没有 Three.js、游戏引擎、图片、字体文件或音频素材，下载 `index.html` 即可运行。
- **程序化美术**：鹈鹕、自行车、海岸、棕榈、山脊、灯塔、帆船、海面、天空和 UI 全部在运行时生成。
- **动画**：踏板 IK、车轮转动、身体起伏、转弯压弯、动态丝绸围巾、海面高光、漂浮粒子、鱼群微光。
- **固定 120 Hz 模拟**：渲染帧率与玩法更新分离；每帧最多补算有限步数，避免卡顿后发生穿模。
- **连续碰撞检测**：障碍在每一步使用「本帧扫过的 z 区间」与骑手碰撞盒求交，低帧率下也不容易穿过薄障碍。
- **公平障碍生成**：每行最多占用两条车道；相邻两行的所有安全车道必须能在一次变道内到达。下一条安全路线永远存在。
- **响应式与性能**：桌面和手机自适应；小屏幕限制渲染像素比；1440×900 实测约 60 FPS。
- **合成音效**：海浪、风声、拾取、碰撞、倒计时和结算音全部由 WebAudio 现场合成。

## 本地运行

1. 直接双击 `index.html`，或拖进支持 WebGL2 的现代浏览器。
2. 也可以启动一个静态服务器：

```bash
python -m http.server 8080
```

然后访问 <http://localhost:8080/>。不需要安装依赖或执行构建。

### 发布到 GitHub Pages

把仓库推送到 GitHub 后，在 `Settings → Pages → Build and deployment` 中选择：

- Source: **Deploy from a branch**
- Branch: **main**
- Folder: **/ (root)**

保存后即可通过 `https://<你的用户名>.github.io/<仓库名>/` 游玩。

## 模型评测

这个仓库也是一个小型模型能力样本。

| 项目 | 内容 |
| --- | --- |
| 日期 | 2026-10-17 |
| 代码环境 | DeepSeek Harness |
| 测试模型 | `<上传前填写模型名称 / 版本>` |
| 交付形态 | 单 HTML，无外部依赖 |

当前版本记录在 [EVALUATION.md](EVALUATION.md) 中：

- 在完整需求下从零完成方案、3D 场景、角色、玩法、UI、音效和移动端适配
- 自动化验证：碰撞、掉心、死亡结算、暂停/恢复、重开、本地最高分
- 自动化验证：连续 35 组障碍的路线可达性
- 运行验证：Chrome + WebGL2，1440×900 下约 60 FPS，无控制台错误

### 调试接口

页面暴露了一个仅供测试使用的对象 `window.__pelicanCoast`：

```js
window.__pelicanCoast.getState();          // 当前状态
window.__pelicanCoast.start();             // 从开场画面开始
window.__pelicanCoast.skipCountdown();     // 跳过倒计时
window.__pelicanCoast.advance(5);          // 快进 5 秒玩法
window.__pelicanCoast.setSpeed(24);        // 设置速度
window.__pelicanCoast.setInvincible(999);  // 测试/演示用
window.__pelicanCoast.moveLane(1);         // 左/右变道目标
window.__pelicanCoast.pause();
window.__pelicanCoast.resume();
```

它不是一个稳定的公开 API，仅用于自动化截图和玩法验证。

### 想用新模型重新生成一份？

给模型同一份需求（单文件 3D 鹈鹕骑车游戏、可调速、可躲避、动画唯美、碰撞和障碍生成准确），然后对比：

1. 是否真的能直接玩，还是一运行就报错
2. 视觉是否有统一的艺术方向
3. 障碍是否会出现无路可走的死局
4. 高帧率 / 低帧率下碰撞是否稳定
5. 是否处理了移动端、暂停、结算、重开等完整流程

## License

[MIT](LICENSE) © 2026 xu-shiwei66

---

如果这个项目对你有帮助，欢迎点一个 Star，或者用它来对比你正在测试的新模型。
