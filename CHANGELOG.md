# 更新日志

## v1.0.9（2026-10-01）

- **安装包瘦身**：包内更新日志只带最近 5 版（更早的更新记录仍在本插件仓库里）——由 SDK 自动施加，用户无需任何操作。

## v1.0.8（2026-09-30）

- **自有翻译归位（E6#161「谁的仓谁译文」）**：本仓首次带自己的字典 `i18n/en.json` ＋ `contributes.i18n` 声明——插件名与声明的英文译名住本仓，不再依赖 `lang-defaults` 代管（跨仓追不上：文案在本仓声明、译名却在别的仓的字典里）。
- **判据随 SDK 下发**：`@linkdesk/plugin-sdk` ^0.1.19 → **^0.1.61**——`npm run verify` 第 ⑧ 段「自有字典覆盖度」（manifest 渲染串缺口 🔴 / 源码 `t()` 缺口 ⚠️）由 `@linkdesk/plugin-sdk/own-dict-coverage` 判定（判据本体在 SDK，⛔ 不在本仓复制）。

## v1.0.7（2026-09-30）

- **README 里的场景封面「补全的窗」回来了**：`resources/cover.svg` 用了 `&nbsp;`——XML 只有 5 个预定义实体
  （`amp`/`lt`/`gt`/`quot`/`apos`），`nbsp` 不在其中 ⇒ **整份 SVG 解析失败**。市场详情页会把插件 README 的相对
  图片解析到包内（`linkdesk://python/…`），所以这张图在详情页与 GitHub 上都是**一枚破图，且不报任何错**
- 改用数字字符引用 `&#160;`（同一个不换行空格字符），断行与排版逐字不变
- 同类隐患起闸（E6#160）：`@linkdesk/plugin-sdk` 新增 `svg-wellformed` 子路径（严格 XML 解析器说行才算行），
  本仓 `npm run verify` 随之多出**第 ⑦ 段**——本版过闸读数 = 七段全绿

## v1.0.6（2026-09-15）

- **分发件补上 MIT LICENSE**：`LICENSE` 早就在本仓里（E6#108g 那批加的），但**已发布的那版产物比它早** ⇒ 用户手上那份 zip 里一直没有版权声明。MIT 要求「副本里带声明」，而 zip 才是用户真正拿到的那份
- **不再夹带仓库面文件**：`@linkdesk/plugin-sdk` 升到 0.1.19（^0.1.14 → ^0.1.19）——旧 SDK 的打包通道会把 `marketplace.json` / `scripts/ci-verify.mjs` / `AGENTS.md` 这类**仓库面文件**一起装进 zip（那是给仓库看的，不是给用户看的），0.1.19 的排除表已覆盖
- 无功能变化——本版只为让「用户拿到的产物」与仓库对齐

## v1.0.5（2026-09-14）

- 源码迁入独立仓（E6#99，L7 第 7.2 轮）——从壳仓 `Encaron/linkdesk` 抽出本插件子树，历史全保（hash 变）
- 随包 `plugin.json` 显式声明 `pluginId`（E6#98g）：插件身份不再靠目录名兜底，独立仓构建出的包名与身份稳定
- `$schema` 改指本仓 `node_modules/@linkdesk/plugin-sdk`（脱离壳仓后原相对路径指到仓外，编辑器补全/校验会失效）


## v1.0.4（2026-09-11）

- 更新记录迁入包内的 `CHANGELOG.md`（E6#92 元数据归一）——此前写在 `plugin.json` 的 `changelog` 字段里，市场详情页读不到

## v1.0.2（2026-09-09）

- 图标身份分工（E6#69 三图模型）：新增 icon=resources/icon.svg（Type-2 彩色身份图），撤 marketIcon=cover.svg——整幅封面迁入 README 展示
