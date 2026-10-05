# 更新日志

## v1.1.1（2026-10-06）

- **图标清单的「图纸」搬回本仓（自足性收口）**：转换 material 图标集的那只脚本原先住在 LinkDesk 壳仓（`scripts/convert-material-icons.mjs`），本仓只留产物 ⇒ 换人／换机想加一批图标，得先去壳仓改那只脚本（而壳仓不是作者的仓）。现在同一件事由 **`@linkdesk/plugin-sdk` 的 `import-icon-theme` 命令**做（公开 npm，**任何图标主题作者可用**），而**本主题「选哪些图标」的编辑决定**住本仓 **`icon-import.json`**（三张表 ＋ 两条改指 ＋ 自绘资产白名单）。
  - 重跑（例如升上游 material-icon-theme）：`npm pack material-icon-theme` → 解包 → `npm run icons:import -- package/dist/material-icons.json`。本次实测：产物与现 `icons/pastel.json` **逐字节一致**（303 条映射 / 180 个 SVG 全部对上）。
  - `package.json` 的 devDep `@linkdesk/plugin-sdk` 随之抬到 `^0.1.84`（`import-icon-theme` 自该版起可用）；壳仓侧同笔撤掉 `icons:convert` 入口与那只脚本——**⛔ 不再有「图纸住壳仓」这回事**。
- **功能零变更**：图标、映射、配色、id、显示名一律未动——升级后看到的图标与 v1.1.0 完全一样（本次只动工具链与说明）。

## v1.1.0（2026-10-05）

- **图标覆盖大扩档**：原精选偏「语言生态」，Windows 桌面与嵌入式的日常文件一概命中不了（`.exe` / `.docx` / 压缩包 / 工程配置全落回默认文件图标）。本次从上游 material-icon-theme 扩到 **303 条映射 / 180 个彩色 SVG**（原 139 条 / 99 个），新增 **122 个扩展名 + 42 个文件名**：
  - **可执行与二进制**：`.exe` `.msi` `.dll` `.so` `.lib` `.a` `.o` `.obj` `.bin` `.hex` `.wasm` `.jar` `.class` `.apk` `.iso` `.deb` `.rpm` `.dmg` `.vmdk`…
  - **Office 与电子书**：`.docx` `.doc` `.xlsx` `.xls` `.pptx` `.ppt` `.odt` `.ods` `.odp` `.rtf` `.epub`（`.xlsx` 走上游 `table` 图标、`.pptx` 走 `powerpoint`）
  - **压缩包**：`.zip` `.rar` `.7z` `.tar` `.gz` `.bz2` `.xz` `.tgz` `.zst` `.cab`
  - **字体与媒体**：`.ttf` `.otf` `.woff` `.woff2` `.eot`、`.psd` `.ai` `.fig` `.sketch`、`.mp3` `.mp4` `.wav` `.avi` `.mkv` `.mov` `.flac` `.heic` `.avif`…
  - **语言扩充**：汇编 `.asm`/`.s`、Verilog `.sv`/`.svh`/`.vhd`/`.vhdl`、GraphQL、Proto、Prisma、Elixir、Erlang、Clojure、Haskell、Julia、Nix、Perl、Pug/EJS/Handlebars/Twig、Astro、Solidity、Zig、Nim、Groovy、F#、VB、Lisp、Tcl、CoffeeScript…
  - **数据**：`.ipynb`（Jupyter）、`.sqlite` `.db` `.mdb`、`.parquet` `.pkl`、`.tf`/`.hcl`（Terraform）
  - **工程配置（按文件名）**：`.prettierrc` `.eslintrc` `.babelrc` `.clangd` `.nvmrc` `yarn.lock` `pnpm-lock.yaml` `Gemfile` `Rakefile` `Justfile` `Jenkinsfile` `.travis.yml` `.bazelrc` `favicon.ico` `robots.txt` `.gitmodules` `.htaccess`…
  - **文档（按文件名）**：无扩展名的 `README` / `CHANGELOG`、`CONTRIBUTING.md`、`TODO.md`、`AUTHORS`、`SECURITY.md`、`CODE_OF_CONDUCT.md`、`LICENSE.txt`
- **新增一枚本仓自绘图标** `icons/material/uvprojx.svg`（**全仓唯一非上游资产**，MIT © Encaron）——给 Keil μVision 的 `.uvprojx`/`.uvproj`/`.uvopt`/`.uvoptx`。**上游两个主流图标包都没有 Keil 图标**：material-icon-theme 5.39.0 与 vscode-icons 都在 GitHub 上逐条查过、零命中（vscode-icons 那个 `file_type_uv` 是 Python 的 uv 包管理器，与本主题无关）⇒ 按 material 的扁平风格自绘一枚单片机图标（绿芯 + 12 引脚），不涉第三方商标资产。
- **两条本地改指**（住转换脚本 `EXTENSION_OVERRIDES`，每条随码注明理由）：`.o`/`.obj` 上游归给 `3d`（那是给 Wavefront 3D 模型的）——工程语境里它们是编译目标文件，改指 `lib`（跟着 `.a`/`.lib` 走「库 / 目标文件」）。
- **一条不收**：`.v` —— 上游归给 V 语言，而嵌入式的 `.v` 常是 Verilog，两个解释都成立 ⇒ 不收，宁可回退默认文件图标（`.sv`/`.svh`/`.vhd`/`.vhdl` 照收）。
- **不动的东西**：图标主题 id、显示名（`label`/`name`）、配色、上游 SVG 资产本身——原有 139 条映射**一字未改，只增不改**；老用户升级后看到的图标只会**变多**，不会变样。
- 壳仓侧同笔更新转换脚本 `scripts/convert-material-icons.mjs`（清单扩充 ＋ `EXTENSION_OVERRIDES` ＋ `LOCAL_EXTENSIONS`）；该脚本住壳仓，本仓只留产物。

## v1.0.6（2026-10-01）

- **图标主题显示名去双语化**：`contributes.iconThemes[].label` 由双语字面量「粉彩图标集 Pastel Icons」改为**纯中文**「粉彩图标集」——按「谁声明谁译文」正典，字面量只写源语言，英文译名住**本仓字典** `i18n/en.json`（该键原值 `Pastel Icon Set`，**键与值一字未改**）。
- **触发**：壳侧 `app.iconTheme` 下拉打通显示面（从「只列原始 id」改为「id ＋ 显示名」，`label` 经 `enumDescriptions` 进设置页、由设置页 `t()` 解析）——`label` 从「零消费方」变成用户看得见的一行，双语字面量到此才会真的露到界面上。
- **判据随 SDK 下发**：`@linkdesk/plugin-sdk` ^0.1.61 → **^0.1.66**——`contributes.iconThemes[].label` 从**豁免**改为**可渲染串**（显示面打通 ⇒ 同笔纳入），漏译由 `npm run verify` 第 ⑧ 段判红；本仓该条已住字典。
- 零行为变化：图标数据 / 图标 id / 其余文案一字未动。

## v1.0.5（2026-09-30）

- **自有翻译归位（E6#161「谁的仓谁译文」）**：本仓 2 条可渲染文案的英文译名住进**本仓字典** `i18n/en.json`（新增 2 条） ＋ `contributes.i18n` 声明——不再依赖 `lang-defaults` 代管：文案在本仓声明、译名却在别的仓的字典里，本仓加一条声明那只仓无从跟上（跨仓追不上）。译名取值：池里现成的照抄（同键同值 ⇒ 按 E6#161「同值覆盖不出声」规则运行时零变化），池里没有的 2 条新写。
- **判据随 SDK 下发**：`@linkdesk/plugin-sdk` ^0.1.19 → **^0.1.61**——`npm run verify` 第 ⑧ 段「自有字典覆盖度」（manifest 渲染串缺口 🔴 / 源码 `t()` 缺口 ⚠️）由 `@linkdesk/plugin-sdk/own-dict-coverage` 判定（判据本体在 SDK，⛔ 不在本仓复制）。

## v1.0.4（2026-09-17）

- **E6#111n-6 外观族 id 带归属**（本轴「非样式命名空间归一化」清账 · 主题族）——本仓名额全在下面；**词干一字未动**，只加了「<插件 id>.」归属前缀：
- 图标主题 id `ld-iconset-pastel` → `theme-iconset-pastel.ld-iconset-pastel`
- 🔴 **显示名（`label` / `name`）一字未动** —— 设置页看到的主题名与配色名**没有变化**；主题的颜色 / 玻璃 / 字体等一切外观内容也**一字未动**（这是「改名 ≠ 改样子」的机械保证）。
- ⚠️ **图标主题 id 走**它自己那张表（独立 id 空间：既不进配方表、也不进配色表）——`normalizeIconThemeId` 是唯一的归一入口。
- **旧 id 不会被丢**：壳侧读时归一（`normalizeRecipeId` / `normalizeColorwayId` / `normalizeIconThemeId`，**解析器门控**＝新名在册且旧名不在册才映）＋ 配置迁移**版本 12** 把盘上的旧值改写掉；用户已选的主题 / 配色 / 图标主题在升级后**照旧生效**（含「插件比壳晚到」的顺序，两问门控保证任一时刻都只有一种解释成立）。

## v1.0.3（2026-09-15）

- 新增市场身份图 `resources/icon.svg`（Type-2 彩色身份图，E6#68a）——此前 `plugin.json` 没有 `icon` 字段，市场里显的是**统一默认彩块**
- 意象：2×2 四枚粉彩瓦片缝成格，说的是「一套图标」而不是「一枚」
- 形态照 [06-图标.md](https://github.com/Encaron/linkdesk/blob/electron/docs/02-Electron%E6%9E%B6%E6%9E%84/E6_%E6%8F%92%E4%BB%B6%E7%94%9F%E6%80%81%E4%B8%8E%E5%8F%91%E5%B8%83/03-%E6%8F%92%E4%BB%B6%E5%B8%82%E5%9C%BA/06-%E5%9B%BE%E6%A0%87.md)：SVG / 透明底 / 48×48 正方形 viewBox / 零 `<text>`（不绑字体）

## v1.0.2（2026-09-15）

- 配方 `$schema` 改**文档唯一认可的写法**（`./node_modules/@linkdesk/plugin-sdk/schemas/theme.schema.json`，相对工程根）——原来用的是已作废的越界相对路径（`../..` 一路指到壳仓 `public/schemas/`，脱离壳仓后编辑器的补全与校验全失效）
- 分发件随包带 **MIT 许可证**（`LICENSE`）——MIT 要求副本里带版权声明，而 zip 才是用户真正拿到的那份
- 新增 `AGENTS.md`：在这个仓里单开 AI 干活时的进场说明（这只插件是什么 / 规矩在哪 / 命令怎么敲）
- 上游许可正本改名保留（`LICENSE-material-icon-theme.md`，MIT © Material Extensions）——本仓自己的许可是 `LICENSE`
- README 订正：转换脚本 `convert-material-icons.mjs` **不在本仓**（住 LinkDesk 壳仓 `scripts/`）

## v1.0.1（2026-09-14）

- 源码迁入独立仓（E6#99，L7 第 7.2 轮）——从壳仓 `Encaron/linkdesk` 抽出本插件子树，历史全保（hash 变）
- 随包 `plugin.json` 显式声明 `pluginId`（E6#98g）：插件身份不再靠目录名兜底，独立仓构建出的包名与身份稳定
- `$schema` 改指本仓 `node_modules/@linkdesk/plugin-sdk`（脱离壳仓后原相对路径指到仓外，编辑器补全/校验会失效）
