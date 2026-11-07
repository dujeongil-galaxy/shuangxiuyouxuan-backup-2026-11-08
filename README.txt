# 站点静态存档

- 源站：https://shuangxiuyouxuan.com
- 存档时间：2026-11-07T16:55:02.108Z
- 工具：site-archiver.cjs（BFS 全量镜像，URL 路径原样映射为目录）
- 处理 URL：867 个（HTML 页面 838 个，资源 32 个）
- 总大小：21.9 MB
- 失败：0 个（详见 archive-report.json）

## 如何查看

用任意静态服务器打开本目录，例如：
```
cd 本目录
npx serve .        # 或 python -m http.server 8080
```

## 说明

- 站外链接（招聘平台、淘宝等）未下载，点击后会跳转到原网站；存档内仅保留链接。
- 客户端渲染的数据（如有）以原始 API JSON 形式存于 _api/ 目录，网页壳页与其配套。
- 详细 URL 清单见 manifest.jsonl。

## 本次存档备注

- 岗位列表与详情数据来自站点 API /api/community/jobs（页面为客户端渲染），已全量存为 JSON（_api/community/jobs/）。
- 共 12000 个岗位，API 数据与岗位页 HTML 壳一一对应。
