# 参与 & 贡献

## 需求

参与本项目需要一点点的 `dom` 知识以及 `chrome devtool` 的使用经验，因为你可能需要深入网站的 HTML 结构中发掘你要翻译的内容或节点。

## 如何开始

本小节将介绍如何进行翻译工作，请确保你本地已经完成了开发环境的搭建。

注意：所有的翻译内容都被存放与 `src/pages/` 目录下。

**步骤一**：复制 `src/pages/template.ts` 文件并命名为你需要翻译的页面名，该页面中包含了一些较为常用的翻译用例。

**步骤二**：之后，在 `src/pages/index.ts` 中引入并统一导出你的文件，否则翻译模块将无法发现你新增的翻译内容：

```diff
import homePage from './homePage'
+ import overview from './overview'

export default [
    homePage,
+   overview,
]
```

**步骤三**：打开你刚刚新建的 `src/pages/xxx.ts` 文件，并修改其中的 `hashs` 字段，该字段是一个数组，请确保你要翻译的页面的 hash 值（*url 中以 `#` 开头的字符串* ）被包含在其中，这样你的翻译内容才可以被正确的匹配到对应的页面上：

```diff
const content: PageContent = {
-   hashs: [ '' ],
+   // 匹配所有 hash 以 #!/sim 开头的页面
+   hashs: [ '#!/sim' ],
    content: [
        // ...
    ]
}

export default content
```

**步骤四**：之后就可以按照文件 `content` 字段中包含的示例进行翻译啦。

## 提交 Pull Request

如果你想要提交一个 PR 的话，请按照以下流程进行：

- 请确保你本地可以正常运行该项目。
- 请勿修改 `src/pages/` 之外的代码，除非你清楚自己在做什么。
- 请在翻译完成后通读一遍来确定没有错别字等问题。
- 请解决完所有的冲突（优先使用 `rebase`）后再提交 PR。
- 请确保你的 commit message 以如下字段开头：
    - `feat:` 新的框架功能
    - `fix:` 框架问题修复
    - `translate:` 新内容汉化
    - `polish:` 润色及错误勘正

提交完成后我们会进行审核并合并你的 PR，并将你的信息加入到本项目的鸣谢列表中😘。