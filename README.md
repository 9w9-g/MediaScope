# 2026 暑期档游戏媒体画像横评

21 家游戏行业垂类公众号，2026-06-01 至 08-31，基于付费采集的文章与真实互动数据产出的内容洞察报告。

## 站点内容

| 文件 | 说明 | 体积 |
|---|---|---|
| `index.html` | 站点入口，两个报告的导航页 | 7 KB |
| `2026暑期档游戏媒体内容洞察与约稿建议_v27.html` | 主报告，含 21 张交互图表 | 9.2 MB |
| `2026暑期档游戏媒体画像_v27.html` | 21 家媒体逐家画像子页 | 0.65 MB |
| `assets/ms-logo.png` | MediaScope 平台标识 | 27 KB |

两个报告之间用同目录相对文件名互相跳转，**改名或拆目录都会断链**。

## 口径要点

- 采集 4,282 篇，排除 77 篇后有效分析样本 4,205 篇，有正文样本 4,188 篇。
- 爆款按各家自有的号内前 10% 界定，全档 513 篇，基准 12.2%。各家量级差异很大，**号内数字不跨号比较**。
- 阅读数达到 10 万的稿件由接口封顶返回，全档 85 篇，只计篇数，不参与排序与中位数计算。
- 报告只给数据对比与素材要求，不下投放决策。

## 部署

站点地址：https://9w9-g.github.io/MediaScope/

`main` 分支是源，`gh-pages` 分支是发布分支（Pages 的 Source 设为 `Deploy from a branch` + `gh-pages` + `/ (root)`）。当前用 gh-pages 分支直推发布，没有启用 GitHub Actions。

更新报告后三步：

```bash
# 1. 提交到 main
git add -A && git commit -m "更新报告"

# 2. 让 gh-pages 指向 main 的最新提交
gh api -X PATCH /repos/9w9-g/MediaScope/git/refs/heads/gh-pages \
  -f sha=$(git rev-parse main)

# 3. 触发构建（首次构建常卡住，手动触发更可靠）
gh api -X POST /repos/9w9-g/MediaScope/pages/builds
```

构建约 40 秒完成。若 `git push` 被环境拦截，第 1 步可改用 GitHub 网页上传或 contents API。

## 注意

主报告单页约 9 MB，首次打开需要几秒。
