# luanfuzi-blog

Luan_Fuzi 的个人博客源码仓库。

📖 博客地址：**[https://luanfuzi.top](https://luanfuzi.top)**

## 项目来源

本博客基于开源主题 [**Firefly**](https://github.com/CuteLeaf/Firefly)（一款清新美观的 Astro 静态博客主题，Astro 7 + Svelte 5 构建，是 Fuwari 的扩展分支）搭建，并做了大量定制：

- 删除了主题自带的所有演示内容（演示文章、动态、友链、打赏、看板娘、壁纸等）
- 保留了主题核心功能：评论系统、音乐播放器、搜索、代码高亮、Mermaid/PlantUML 图表、相册、动态、书签导航、i18n 等
- 所有站点配置集中在 `src/config/`（配置项说明见 `src/config/README.md`）

## 技术栈

| 项目 | 说明 |
|------|------|
| 框架 | Astro 7（静态输出到 `dist/`） |
| 交互组件 | Svelte 5 |
| 样式 | Tailwind CSS 4 |
| 搜索 | Pagefind（构建时生成索引） |
| 字体 | Astro Font API（fontsource） |

## 本地构建

要求：Node.js >= 22，包管理器为 pnpm。

```bash
pnpm install    # 安装依赖
pnpm dev        # 开发服务器 http://localhost:4321
pnpm build      # 生产构建：LQIPs → Astro build → 字体子集化 → Pagefind 索引
pnpm preview    # 本地预览构建产物
pnpm check      # 类型检查
pnpm lint       # Biome 检查
pnpm new-post <文件名>   # 新建文章
pnpm new-dynamic        # 新建动态（微博客）
```

文章写在 `src/content/posts/`，动态在 `src/content/dynamic/`（用上面的脚本创建），图片放在 `public/imgs/posts/<文章名>/`。

## 为什么选择 Cloudflare

- **免费额度够用**：Workers 免费套餐对个人静态博客完全足够
- **Git 自动部署**：Workers Builds 连接 GitHub 仓库后，push 自动触发构建部署，无需手动操作
- **全球 CDN**：静态资源分发到 Cloudflare 全球边缘节点
- **免费 HTTPS + 自定义域名**：自动签发证书，无需额外配置
- **DNS 一体化**：域名 DNS 也托管在 Cloudflare，和 Workers 同一处管理

## 发布流程

```
git push（main 分支）
  → GitHub 向 Cloudflare 发送 webhook
  → Workers Builds 拉取代码，执行构建命令 pnpm build（产出 dist/）
  → 执行部署命令 npx wrangler deploy，按 wrangler.jsonc 部署静态资源
  → https://luanfuzi.top 生效（约 1-2 分钟）
```

Workers Builds 项目配置（Cloudflare Dashboard → Workers & Pages → luanfuzi-blog）：

| 配置项 | 值 |
|--------|-----|
| 生产分支 | `main` |
| 构建命令 | `pnpm build` |
| 部署命令 | `npx wrangler deploy`（默认） |

部署配置在仓库根目录的 `wrangler.jsonc`（Worker 名称 `luanfuzi-blog`、静态资源目录 `./dist`），删掉它会导致构建失败。

## 域名

| 项目 | 信息 |
|------|------|
| 域名 | `luanfuzi.top` |
| 注册商 | Spaceship（https://www.spaceship.com/） |
| 注册时间 | 2026-08-03 |
| 到期时间 | 2031-08-03 |
| DNS 托管 | Cloudflare（NS: `janet.ns.cloudflare.com` / `fred.ns.cloudflare.com`） |

域名在 Spaceship 购买后，将 DNS 名称服务器改到了 Cloudflare（Cloudflare Dashboard → 添加站点），并在 Cloudflare Pages 项目中绑定了自定义域名 `luanfuzi.top`。续费在 Spaceship 控制台操作。
