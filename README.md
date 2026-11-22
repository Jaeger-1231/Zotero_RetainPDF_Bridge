<p align="center">
  <img src="assets/icon.png" alt="Zotero_RetainPDF_Bridge" width="128" />
</p>

<h1 align="center">Zotero_RetainPDF_Bridge</h1>

将 **Zotero 7+** 与本地 **RetainPDF** 桌面端无缝桥接的插件：在 Zotero 中一键调用 RetainPDF 进行保留排版（公式、图表、多栏布局）的学术文献翻译，并自动将**双语对照版 PDF（`contrast.pdf`）**与**译文版 PDF（`translated.pdf`）**挂回对应文献条目。

## 功能特性

- **右键一键翻译**：在 Zotero 文献条目上右键直接发送至本地 RetainPDF 翻译。
- **自动回挂译文附件**：翻译完成后自动下载并挂载以下两个附件到 Zotero 原文献条目下：
  - `contrast.pdf`：双语对照版 PDF
  - `translated.pdf`：单语译文版 PDF
- **内置任务中控台**：在 Zotero 顶部工具栏查看翻译队列与历史任务，支持一键跳转 RetainPDF 详情页。
- **支持手动回挂**：中控台已完成任务卡片提供「挂回选中条目」按钮，可将历史翻译结果（`contrast.pdf` 与 `translated.pdf`）手动挂回当前选中的 Zotero 文献。
- **兼容新版 RetainPDF 桌面端**：默认适配 `127.0.0.1:41000` 后端端口及 `X-API-Key` 鉴权。

---

## 使用前准备

1. 已安装 **Zotero 7** 或更高版本。
2. 已安装并启动本机 **RetainPDF 桌面端**（推荐 `2026.11.22` 及以上版本）。
   - macOS 首次安装如遇“应用已损坏/无法打开”，可在终端执行：
     ```bash
     sudo xattr -r -d com.apple.quarantine /Applications/RetainPDF.app
     ```
3. 已准备好 OCR 凭证（PaddleOCR / MinerU）与翻译大模型 API Key（DeepSeek 或自定义 OpenAI 兼容接口）。

---

## 安装与配置步骤

### 1. 安装插件
1. 前往本仓库 [Releases](https://github.com/Jaeger-1231/Zotero_RetainPDF_Bridge/releases) 页面下载最新的 `Zotero_RetainPDF_Bridge-x.x.x.xpi`。
2. 打开 Zotero → 顶部菜单 **工具（Tools）→ 插件（Plugins）**。
3. 点击右上角齿轮图标 → **从文件安装插件（Install Plugin From File...）**，选择下载的 `.xpi` 文件。
4. **完全退出并重启 Zotero** 使插件生效。

### 2. 配置插件参数
1. 保持本机 **RetainPDF 桌面端处于运行状态**。
2. 打开 Zotero **设置（Settings）→ RetainPDF** 面板：
   - **服务地址**：填写 `http://127.0.0.1:41000`（默认已填好），点击右侧 **检查连接** 确认通过。
   - **OCR 识别**：选择 PaddleOCR 或 MinerU 并填入对应 Token，点击 **检查连接** 验证。
   - **翻译模型**：填写 DeepSeek 或自定义 API 地址、API Key 及模型名称，点击 **检查连接** 验证。

---

## 日常操作指南

### 1. 翻译文献并自动回挂
1. 在 Zotero 文献列表中选中目标文献，**右键**选择 **RetainPDF 翻译**。
2. 等待翻译完成（可在顶部工具栏打开 **RetainPDF 中控台** 查看进度）。
3. 完成后展开该文献条目左侧的 `>` 箭头，即可看到自动挂回的附件：
   - **`contrast.pdf`**：双语对照版 PDF
   - **`translated.pdf`**：译文版 PDF
   双击任意附件即可在 Zotero 内直接阅读和做笔记。

### 2. 使用中控台查看详情与手动回挂
- 点击 Zotero 工具栏中的 **RetainPDF 中控台** 图标即可打开任务列表。
- **查看网页对照页**：点击任务卡片右下角的 **「查看详情」**，将在浏览器中打开 RetainPDF 本地阅读页（`http://127.0.0.1:40001/detail.html?...`）。
- **手动回挂历史任务**：
  1. 先在 Zotero 主界面单击选中目标文献条目；
  2. 在中控台找到对应的已完成任务，点击 **「挂回选中条目」**，即可将 `contrast.pdf` 和 `translated.pdf` 挂回该文献下。

---

## 常见问题

- **连接失败 / 校验不通过**：确认 RetainPDF 桌面端已启动，且插件内服务地址为 `http://127.0.0.1:41000`（而非前端页面端口 `40001`）。
- **在 RetainPDF 桌面端里看不到 Zotero 刚翻译的文献**：切到 RetainPDF 窗口按 `⌘ + R`（Windows 按 `Ctrl + R`）刷新文库列表即可显示。
- **自定义桌面端 API Key**：插件默认使用桌面端内置密钥 `retain-pdf-desktop`。若服务端修改了密钥，可在 Zotero **设置 → 高级 → 编辑器** 中修改 `extensions.zotero.retainpdf.apiKey`。

---

## 致谢

- 感谢 [RetainPDF](https://github.com/wxyhgk/retain-pdf) 作者及开源社区提供了优秀的保留排版学术 PDF 翻译工具。
- 感谢 [Zotero](https://www.zotero.org/) 及其插件开发生态支持。

## License

本项目采用 [MIT License](LICENSE) 开源协议。
