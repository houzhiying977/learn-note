---
title: webpack 常用配置
tags: webpack 打包
notebook: webpack
---

<!-- TOC -->

- [常用 loaders](#常用-loaders)
- [常用插件](#常用插件)
- [自动热更新](#自动热更新)
- [文件指纹](#文件指纹)

<!-- /TOC -->

## 常用 loaders
- /.js$/
```
babel-loader                       -- 解析 es6 语法
thread-loader                      -- 多线程解析
```
- /.css$/
```
MiniCssExtractPlugin.loader        -- 单独提取 css 文件
style-loader                       -- 将 css 动态注入 head 元素
css-loader                         -- 解析 css 文件
postcss-loader                     -- 自动添加兼容性 css
px2rem-loader                      -- 把 px 编程 rem
```
- /.less$/
```
less-loader                        -- 解析 less 成 css
```
- /.s[ac]ss$/i
```
sass-loader                        -- 解析 scss 成 css
node-sass
```

## 常用插件
```
html-webpack-plugin                 -- html 多页面配置; 压缩 html
mini-css-extract-plugin             -- 单独打包 css 为文件
optimize-css-assets-webpack-plugin  -- 压缩 css
UglifyjsWebpackPlugin               -- 压缩 js
clean-webpack-plugin                -- 每次打包时候清除 dist 文件
copy-webpack-plugin                 -- 静态资源输出
friendly-errors-webpack-plugin      -- 优化错误提示
speed-measure-webpack-plugin        -- 测量 loader 和 plugin 打包时间
webpack-bundle-analyzer             -- 打包大小分析
happypack                           -- 多线程打包
terser-webpack-plugin               -- 多线程压缩
hard-source-webpack-plugin          -- 打包产生缓存
purgecss-webpack-plugin             -- 删除没用的 css
image-webpack-loader                -- 图片压缩
```

## 自动热更新
```
webpack-dev-server                  -- 一般场景使用
webpack-dev-middleware              -- 灵活场景使用
```

## 文件指纹
```
hash                                -- 每次重新构建项目重新生成 hash
chunkhash                           -- 和 webpack 打包的 chunk 有关，不同 entry 会生成不同的 chunkhash 值
contenthash                         -- 根据文件内容定义 hash, 文件内容不变，那么 contenthash 也不变
```
