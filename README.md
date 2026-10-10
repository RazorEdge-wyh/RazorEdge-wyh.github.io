# 王越豪 · RazorEdge

个人主页源码 —— 线上地址：**https://razoredge-wyh.github.io/**

纯静态站点，零依赖、零构建：原生 HTML / CSS / JavaScript，克隆下来直接打开 `index.html` 就能看。

另有「创新班选拔作品展示」站：https://razoredge-wyh.github.io/my-site/
两个站点共用同一份内容源，`content.js` 与 `style.css` 在两个仓库中保持一致。

## 文件说明

| 文件 | 作用 |
| --- | --- |
| `index.html` | 页面结构（首页、介绍、技能、经历、作品、相册、联系方式） |
| `content.js` | **全部文字内容**：姓名、简介、facts、traits、skills、timeline、works、repos、gallery、联系方式 |
| `render.js` | 极简渲染器：把 `content.js` 的数据填进页面，并处理深/浅色主题切换 |
| `style.css` | 排版样式，全站只有一个强调色变量 `--accent` |
| `images/` | 站点照片（5 张） |
| `.github/workflows/deploy-home.yml` | GitHub Pages 自动部署 |

## 本地预览

```bash
# 方式一：直接双击 index.html
# 方式二：起个本地服务（推荐，避免个别浏览器对 file:// 的限制）
python -m http.server 8000
# 然后访问 http://127.0.0.1:8000
```

## 修改内容

**改文案只需要动 `content.js`。** 页面结构由 `render.js` 负责，一般不用碰。

- 姓名 / 简介 / 标语：`name` `nameEn` `tagline` `intro`
- 首页信息条：`facts`
- 性格与做事方式：`traits`
- 技能：`skills`
- 经历时间线：`timeline`
- 作品与公开项目：`works` `repos`
- 照片：把图片放进 `images/`，再改 `gallery` 里的引用
- 联系方式：`email` `phone` `links`

## 部署

推送到 `main` 分支即自动发布，无需手动操作：

1. GitHub Actions 读取 `.github/workflows/deploy-home.yml`
2. 将仓库根目录作为站点产物上传
3. 通过 GitHub Pages 部署到 https://razoredge-wyh.github.io/

也可以在 Actions 页面手动触发（`workflow_dispatch`）。

## 设计原则

- 文字为主，照片为辅：首页只放小头像，照片集中在文末相册
- 不用卡片、阴影、光晕、渐变网格，只靠字号层级、留白和细分隔线
- 深色 / 浅色主题默认跟随系统，也可手动切换
- 全站只有一个强调色

## 许可

[MIT](LICENSE)