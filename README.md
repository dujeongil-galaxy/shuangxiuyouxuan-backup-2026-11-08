# 双休优选 站点备份（shuangxiuyouxuan-backup-2026-11-08）

> **仅仓库备份：未启用 GitHub Pages，未部署任何站点。**
> 源站：https://shuangxiuyouxuan.com/ ，抓取时间 2026-11-08（GMT+8）。

## 这是什么

第三方站点「双休优选」的全量静态镜像备份。数据版权归原站/原作者所有，本仓库只做存档，
并非官方数据源。页面按 URL 路径原样映射为目录
（`/products/product-648` → `products/product-648/index.html`；查询串页面存成 `index@query.html`）。

## 本次规模

| 项 | 数量 |
| --- | ---: |
| 实际落盘文件 | 879（约 60 MB，含 2 个清单 / 报告元文件） |
| HTML 页面 | 838 |
| 岗位列表 / 详情 | 18,698 / 18,698（站点 total 18,698） |
| 列表分页原始响应 | 935 页（0 基，每页 20 条） |
| 抓取 URL / 失败 | 867 / 0 |
| 校验 | 清单逐文件 SHA-256 一致、站内资源引用 0 缺失、岗位 ID 0 重复 |

> 账号下 2026-10-25 建的 `shuangxiuyouxuan-archive` 只有 5,154 个岗位，是更早的一份存档；
> 本仓库是站点当前的全量数据，两个仓库互不影响（见文末）。

## 目录

- `index.html`、`products/`、`companies/`、`jobs/`、`methodology/` 等：页面镜像
- `_next/`：Next.js 静态资源（CSS / JS）
- 根目录图片：`apple-touch-icon.png`、`icon-192.png`、`beian-police.png`、`favicon.ico`
- `_api/community/jobs/`：
  - `jobs-all.json` — 18,698 条岗位列表项
  - `jobs-details-all.json` — 18,698 条岗位详情（含 description 全文、source_url、双休证据等）
  - `list-pages-all.json` — 935 页列表原始响应，便于复现分页语义
- `BACKUP-MANIFEST.json` — **实际落盘逐文件 bytes / SHA-256 权威清单**
- `manifest.jsonl` — 抓取器原始 URL 日志；其中岗位逐条 JSON 已合并，实际文件以权威清单为准
- `archive-report.json` / `jobs-extra-report.json` / `postprocess-report.json` — 抓取、补抓、合并报告
- `README.txt` — 抓取器自动生成的原始报告（其「总大小」只统计页面与资源，不含 API JSON；
  完整统计以 `postprocess-report.json` 为准）
- `sitemap.xml`、`robots.txt`

## 抓取口径

- 遵守源站 `robots.txt`：BFS 跳过 `/api/`、`/admin/`、`/go/`；站外链接只记录不下载。
- 岗位数据走公开只读 GET `/api/community/jobs`（列表分页 + 详情），**不调用任何写接口**。
  抓取器的列表循环原有 600 页上限（12,000 条），本次已补抓到 935 页、18,698 条全量。
- 岗位详情页是客户端渲染的相同壳页，本次不重复存数千个壳页；数据以 JSON 为准。
- 逐条详情 JSON 与列表分页 JSON 已合并为大文件，控制仓库文件数
  （原始逐条明细记录在 `manifest.jsonl`，合并后单文件已移出仓库，数据无丢失）。
- **未注入任何离线 API 拦截器**：本仓库是纯文件备份，不提供可直接浏览的站点。
  clone 后客户端渲染的岗位列表在离线状态下不会加载，这是预期行为。

## 与其他仓库的关系

本仓库与 `uniquesunshine-backup-2026-11-08` 是同批新建的**两个独立仓库**，各存一个站点，
互不包含。账号下 2026-10-25 建的 `shuangxiuyouxuan-archive` 按站长要求保持原样、未改动。

## 推送记录

- `1754a89`（2026-11-08 01:07:13 +08:00）：初始备份提交，含 838 个 HTML 页面、
  18,698 条岗位列表与详情、935 页列表原始响应、静态资源与全部清单报告。
  本节在下一提交回填该真实哈希，文档不留「待回填」占位；回填后同步刷新
  `BACKUP-MANIFEST.json`，保证清单哈希与落盘文件一致。
- 仓库为 public，但**未启用 GitHub Pages**，不提供任何在线访问。
