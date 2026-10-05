# 粉彩图标集（theme-iconset-pastel）

> 精简彩色图标主题——**Material Icon Theme（material-icon-theme）常用精选集**（MIT，© Material Extensions）。E5.8#133 图标主题闭环实例：彩色 SVG 图像资产形态（`imagePath`）全链应用。

## 能力

| 形态 | 说明 |
|------|------|
| **分类精选集** | 语言生态（js/ts/py/java/go/rs/asm/verilog…）＋ 工程配置（package.json/.prettierrc/.clangd…）＋ Office 文档（docx/xlsx/pptx…）＋ 可执行与二进制（exe/dll/bin/hex…）＋ 压缩包（zip/rar/7z…）＋ 媒体与字体（psd/mp3/ttf…）＋ 数据（sqlite/ipynb/parquet…）= **185 扩展 + 68 文件名 + 25 文件夹名，共 303 条映射 → 180 个彩色 SVG** |
| **默认图标** | `file`/`folder`/`folderExpanded`/`rootFolder`/`rootFolderExpanded` 5 个通用图标——**普通文件夹、新建文件、根文件夹未命中匹配表时也用主题彩色图标**（E5.8#133.6 默认图标链路，对齐 VS Code iconTheme 顶层键） |
| **codicon 保底** | 壳机制内置——极端未覆盖类型回退 codicon 字体保底 |

## 来源与许可

- **图标集**：https://github.com/material-extensions/vscode-material-icon-theme —— MIT 许可（上游许可正本随仓：`LICENSE-material-icon-theme.md`）。
- **获取方式**：`npm pack material-icon-theme`（npm registry）→ `package/dist/material-icons.json`（VS Code iconTheme 格式）+ `package/icons/*.svg`。
- **转换**：`npm run icons:import -- <上游 package/dist/material-icons.json>`（＝ `linkdesk-plugin-sdk import-icon-theme`，随公开 npm 包 `@linkdesk/plugin-sdk` 装——任何图标主题作者都能用同一条命令）——按**分类精选清单**把 VS Code iconTheme 格式转成 LinkDesk 双形态 `imagePath` 格式（含 5 个顶层默认图标），只拷贝被引用的 SVG。
  - 🔴 **本主题「选哪些图标」的编辑决定住本仓 `icon-import.json`**（三张表 ＋ 两条本地改指 ＋ 自绘资产白名单）⇒ 加图标**不必碰任何别的仓**：`npm pack material-icon-theme` → 解包 → 上面那条命令（清单内缺失键静默跳过：映射保留、运行时走保底图标）。
- **⚠️ 唯一非上游资产**：`icons/material/uvprojx.svg` —— Keil μVision 工程图标（`.uvprojx`/`.uvproj`/`.uvopt`/`.uvoptx`），**本仓自绘**（MIT © Encaron，随本插件 `LICENSE`）。上游两个主流图标包都没有 Keil 图标（material-icon-theme 与 vscode-icons 均零命中）⇒ 按 material 的扁平风格自绘，不涉第三方商标资产。
- **两条本地改指**（住 `icon-import.json` 的 `overrides`，理由随清单注明）：`.o`/`.obj` 上游归给 `3d`（3D 模型），本仓改指 `lib`（编译目标文件）。**一条不收**：`.v`——上游归给 V 语言，嵌入式那边常是 Verilog，两个解释都成立 ⇒ 不收，回退默认图标。

## 结构

```
theme-iconset-pastel/
├── plugin.json          # contributes.iconThemes → icons/pastel.json
├── LICENSE              # 本插件的许可（MIT © Encaron）
├── LICENSE-material-icon-theme.md   # 上游图标集的许可正本（MIT © Material Extensions，必须保留）
├── README.md
├── icon-import.json     # 🔴 本仓的**编辑决定**——选哪些扩展名/文件名/文件夹名、两条改指、自绘资产白名单（重跑转换时由 --list 读入）
└── icons/
    ├── pastel.json      # 精选 mappings（303 条 + 5 默认图标，纯 imagePath 形态）
    └── material/        # 彩色 SVG 资产（180 个，仅被引用）
        └── uvprojx.svg  # 唯一非上游资产——Keil 单片机工程图标，本仓自绘
```
