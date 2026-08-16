# picbed

GitHub + jsDelivr 图床：图片提交到本仓库，通过 jsDelivr CDN 加速访问（国内可达）。

## 链接格式

```
https://cdn.jsdelivr.net/gh/Sislecv/picbed@main/images/2026/08/example.png
```

## 使用方式

### 网页上传（推荐）

本机起一个零依赖的上传服务，浏览器（或手机/局域网）拖拽上传：

```bash
upimg-web              # 启动 http://0.0.0.0:8899
upimg-web 9000         # 自定义端口
```

浏览器打开 `http://localhost:8899`，拖拽或点击选择图片（支持多选），自动上传并返回 CDN 链接与 Markdown 格式，一键复制。代码在 `~/upimg-web/`（Python 标准库，无第三方依赖）。

### 命令行（upimg）

```bash
upimg path/to/image.png                 # 上传，输出 CDN 链接并复制剪贴板
upimg -a 截图 a.png b.png               # 批量上传，输出 Markdown 格式
upimg -p images/custom/x.png a.png      # 自定义存放路径
upimg -f a.png                          # 已存在时强制覆盖
```

### PicGo（Typora 等写作工具）

1. 安装 [PicGo](https://github.com/Molunerfinn/PicGo/releases)（Windows/macOS）
2. 图床设置 → GitHub 图床：
   - 设定仓库名：`Sislecv/picbed`
   - 设定分支名：`main`
   - 设定 Token：GitHub → Settings → Developer settings → Personal access tokens → 生成 classic token，勾选 `repo` 权限
   - 指定存储路径：`images/`
   - 自定义域名：`https://cdn.jsdelivr.net/gh/Sislecv/picbed@main`
3. 上传后自动替换为 CDN 链接

## 限制与建议

- jsDelivr 单文件 ≤ 20MB；GitHub 单文件 ≤ 100MB
- jsDelivr 有长期缓存，同名覆盖后刷新慢，**建议文件名不重复（默认按日期分目录）**
- 写作场景图片建议压缩到 800KB 以内，加载更快

## LICENSE

MIT
