# YourLib 条目总览页

`index.html` 是 YourLib 攻击库 / 防御库 / Buff 库的可引用条目总览，单文件、无外部依赖，
可以直接作为静态站点发布。

已发布地址：<https://hbbb1666.github.io/yourlib-entries/>

## 更新页面

页面内容由源码注解生成，不要手改 `index.html`：

```powershell
pwsh -File yourlib\tools\gen-entry-page.ps1
```

这会把同一份内容写到两个地方：

- `docs\yourlib-entries.html` —— 仓库内查看用
- `_site\index.html` —— 发布用（GitHub Pages 认这个文件名）

改完条目或分级后重新生成，再提交推送即可。

## 发布到 GitHub Pages

把本目录作为独立仓库推送，然后在仓库的 Settings → Pages 里把 Source 设为
`Deploy from a branch`、分支选 `main`、目录选 `/ (root)`。约一分钟后可访问：

`https://<用户名>.github.io/<仓库名>/`

注意：直接点开仓库里的 `index.html` 只会看到源码，GitHub 不会渲染 HTML 文件，
必须开 Pages 才会有网页。
