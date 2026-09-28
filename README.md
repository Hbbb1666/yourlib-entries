# YourLib 站点

两个页面，共用 `assets/site.css` 一套样式，都由 `yourlib\tools\gen-site.ps1` 生成，
**不要手改这里生成出来的文件**：

| 文件 | 内容 | 已发布地址 |
| --- | --- | --- |
| `about.html` | 模组详细介绍 | <https://hbbb1666.github.io/yourlib-entries/about.html> |
| `index.html` | 69 条可引用条目总览（带搜索与分级筛选） | <https://hbbb1666.github.io/yourlib-entries/> |

两页顶部互有导航，介绍页的模块卡片会深链到条目页的对应分区。

## 更新

条目页由源码注解生成，介绍页是模板散文，一次命令同时重新生成两页：

```powershell
pwsh -File yourlib\tools\gen-site.ps1
git -C _site commit -am "update pages"; git -C _site push
```

生成器会写四处：

- `_site\about.html`、`_site\index.html`、`_site\assets\site.css` —— 发布用
- `docs\yourlib-entries.html` —— 仓库内查看用的同一份条目页

介绍页的正文在 `yourlib\tools\about-page.template.html`，改文案改那个文件；
条目页的模板是 `yourlib\tools\entry-page.template.html`，样式是 `yourlib\tools\site.css`。

## 发布到 GitHub Pages

把本目录作为独立仓库推送，然后在仓库的 Settings → Pages 里把 Source 设为
`Deploy from a branch`、分支选 `main`、目录选 `/ (root)`。约一分钟后可访问：

`https://<用户名>.github.io/<仓库名>/`

注意：直接点开仓库里的 `index.html` 只会看到源码，GitHub 不会渲染 HTML 文件，
必须开 Pages 才会有网页。
