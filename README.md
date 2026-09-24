# X热榜 · X Hot List

X（Twitter）中文博主人气排行榜：按粉丝数排名，含「福利姬 / 18+ Creators」「私密摄影 / Boudoir」推荐分区，一键直达博主主页。博主可提交收录、分享自己的排名徽章，为主页带来真实流量。

**线上地址 Live**: https://tliens.github.io/xhot/

纯静态单文件站点（`index.html`，内联 CSS/JS，零外部依赖、零构建），中英双语（`?lang=zh` / `?lang=en`），亮暗主题，NSFW 分区需 18+ 确认（仅存本地浏览器）。

## 维护数据 / Update data

所有榜单数据都在 `index.html` 里的 `BLOGGERS` 数组（搜索 `const BLOGGERS`）：

```js
{ h:'handle',        // X 用户名，不带 @（必填）
  n:'显示名',         // 显示名（必填）
  f:128000,          // 粉丝数，纯数字（约数即可）
  c:['flj','photo'], // 分类：flj=福利姬, photo=私密摄影（可多选）
  d:{zh:'简介', en:'bio'},  // 双语一句话简介
  av:'',             // 头像 URL，可留空（留空显示首字母渐变头像）
  add:'2026-09' },   // 收录月份
```

改完 `git push` 即自动重新部署（GitHub Pages，约 1 分钟生效）。

- 删掉 `META.demo = true` 中的 `true`（或整个 demo 标记）即可隐藏"示例数据"提示条。
- 排名自动按 `f` 从高到低计算，不需要手动排序。

## 收录流程 / Submission workflow

1. 访客点击页面上「提交收录」→ 跳转 GitHub Issue 表单（[`.github/ISSUE_TEMPLATE/submit.yml`](.github/ISSUE_TEMPLATE/submit.yml)）
2. 审核申请：确认账号真实、分类合理、勾选了同意项
3. 通过后把博主按上面的格式加进 `BLOGGERS`，push 上线
4. 不通过 / 下架 / 更正：回复对应 Issue 说明原因

## 本地预览 / Local dev

```bash
python3 -m http.server 8971
# open http://localhost:8971
```

## 内容政策 / Content policy

- 仅收录 18+ 平台合规账号；成人向账号需已开启 X 的敏感内容标记
- 收录需博主本人同意；博主可随时通过 Issue 申请修改或下架（通常 48 小时内处理）
- 粉丝数为人工核对的约数，仅供参考；本站与 X Corp. 无关联

## English

X Hot List is a ranked directory of popular Chinese X (Twitter) creators, sorted by follower count, with curated **18+ Creators** and **Boudoir** tabs. Single-file static site, bilingual (zh/en), dark/light themes, 18+ gate for NSFW tabs. Creators submit via the GitHub issue form; approved entries are added to the `BLOGGERS` array in `index.html` and go live on push. Follower counts are manually verified estimates. Not affiliated with X Corp.
