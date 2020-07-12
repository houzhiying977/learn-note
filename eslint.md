
<!-- TOC -->

- [1. 首先安装一下](#1-首先安装一下)
- [创建 eslint 配置文件 .eslintrc.*](#创建-eslint-配置文件-eslintrc)
- [在 rules 中加上 eslint-loader](#在-rules-中加上-eslint-loader)

<!-- /TOC -->

## 1. 首先安装一下
```
npm i eslint eslint-loader babel-eslint -D
```

## 创建 eslint 配置文件 .eslintrc.*
```
// .eslintrc.js
module.exports = {
    // 指定解析器
    'parse': 'babel-eslint',
    // 指定解析器选项
    'parserOptions': {},
    // 继承开源 eslint 规则
    extends: '',
    // 指定脚本的运行环境
    'env': {},
    // 别人可以直接使用你配置好的ESLint
    'root': true,
    // 脚本在执行期间访问的额外的全局变量
    'globals': {},
    // 启用的规则及其各自的错误级别
    'rules': {}
};
```
## 在 rules 中加上 eslint-loader
```
{
        test: /.js$/,
        use: [
            'babel-loader',
            'eslint-loader'
        ]
    },
```

