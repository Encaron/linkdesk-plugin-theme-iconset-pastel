# 更新日志

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
