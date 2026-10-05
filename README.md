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
- **转换**：`convert-material-icons.mjs`——按**分类精选清单**把 VS Code iconTheme 格式转成 LinkDesk 双形态 `imagePath` 格式（含 5 个顶层默认图标），只拷贝被引用的 SVG。⚠️ **该脚本不在本仓**，它住在 LinkDesk 壳仓的 `scripts/` 下（本仓只保留它的产物）。升级 material 版本 = 重新 `npm pack` + 在壳仓重跑转换（清单内缺失键静默跳过）。
- **⚠️ 唯一非上游资产**：`icons/material/uvprojx.svg` —— Keil μVision 工程图标（`.uvprojx`/`.uvproj`/`.uvopt`/`.uvoptx`），**本仓自绘**（MIT © Encaron，随本插件 `LICENSE`）。上游两个主流图标包都没有 Keil 图标（material-icon-theme 与 vscode-icons 均零命中）⇒ 按 material 的扁平风格自绘，不涉第三方商标资产。
- **两条本地改指**（转换脚本 `EXTENSION_OVERRIDES`，理由随码注明）：`.o`/`.obj` 上游归给 `3d`（3D 模型），本仓改指 `lib`（编译目标文件）。**一条不收**：`.v`——上游归给 V 语言，嵌入式那边常是 Verilog，两个解释都成立 ⇒ 不收，回退默认图标。

## 结构

```
theme-iconset-pastel/
├── plugin.json          # contributes.iconThemes → icons/pastel.json
├── LICENSE              # 本插件的许可（MIT © Encaron）
├── LICENSE-material-icon-theme.md   # 上游图标集的许可正本（MIT © Material Extensions，必须保留）
├── README.md
└── icons/
    ├── pastel.json      # 精选 mappings（303 条 + 5 默认图标，纯 imagePath 形态）
    └── material/        # 彩色 SVG 资产（180 个，仅被引用）
        └── uvprojx.svg  # 唯一非上游资产——Keil 单片机工程图标，本仓自绘
```
