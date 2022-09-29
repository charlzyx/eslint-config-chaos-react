## React Eslint 配置
> 自己用的， 在家好找一点

###  配置 eslint

```json
{
  "extends": ["eslint-config-chaos-react"]
}
```

### 安装
```shell
yarn add eslint-config-chaos-react
```
安装后 VSCode ESLint 插件不能够正常工作的话, 问题应该是 `依赖冲突`, 可以安装 peerDependices
到工程跟目录, 或者使用下面这个命令

```shell
npx install-peerdeps eslint-config-chaos-react
```

### 使用
```yaml
extends:
  - "eslint-config-chaos-react"
```

### 依赖冲突
这是一个比较沙雕的问题, 安装包的时候逻辑大概是这样的

项目里面有跟当前 dep 版本冲突的吗?
1. 没有: 直接安装到 跟项目的 node_modeuls (这种情况是没有问题的)
2. 有: 安装到 eslint-config-chaos-react/node_modules (这里就开始有隐患了)

然后在这个配置中, 是有 extends 和使用其他的 plugins 的, 然后 eslint 的配置是根据项目目录的
node_modules 来查找对应插件(参考下方链接), 这时候就会出现找不到的情况, 这种情况下, 就需要很难受的
手动来安装 eslint 所需要的插件到项目的 node_modules 中来处理这种问题

> 当然可以等等 npm@7 的 peerDependices 来处理, 见下方文档

### 参考文档
- [npm 冲突处理逻辑](https://juejin.cn/post/6844904022080667661#heading-49)
- [eslint configuring#configuring-plugins](https://eslint.org/docs/user-guide/configuring#configuring-plugins)
- [npm@7 Automatically installing peer dependencies](https://github.blog/2020-10-13-presenting-v7-0-0-of-the-npm-cli/)

```sh 全量更新
 yarn add @typescript-eslint/eslint-plugin @typescript-eslint/parser babel-eslint eslint eslint-config-prettier eslint-config-react-app eslint-plugin-flowtype eslint-plugin-import eslint-plugin-jsx-a11y eslint-plugin-prettier eslint-plugin-react eslint-plugin-react-hooks prettier
```
