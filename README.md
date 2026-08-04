# Luan_Fuzi 的奇妙冒险

想把可乐带到宇宙去 —— Luan_Fuzi 的个人博客，记录深度学习、编程语言、工具折腾与日常碎碎念。

基于 [Firefly](https://github.com/CuteLeaf/Firefly) 主题（Astro 7 + Svelte 5）构建。

## 开发

```bash
pnpm install
pnpm dev        # 开发服务器 localhost:4321
pnpm build      # 生产构建（LQIPs → Astro build → 字体子集化 → Pagefind 索引）
pnpm preview    # 预览生产构建
pnpm new-post <文件名>      # 新建文章
pnpm new-dynamic           # 新建动态
```

Node.js >= 22，包管理器为 pnpm。

## 目录结构

```
src/content/posts/    # 博客文章
src/content/dynamic/  # 动态（微博客）
src/config/           # 站点配置（所有配置项见 src/config/README.md）
public/               # 静态资源（图片、favicon 等）
```

## 部署

使用 Vercel 部署（`vercel.json`）或 Cloudflare Workers（`wrangler.jsonc`）。

## 许可

博客内容版权归作者所有；代码基于 [Apache License 2.0](LICENSE)（继承自 Firefly 主题）。
