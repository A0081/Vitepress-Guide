# 侧边栏

侧边栏是你文档内容的主要导航，你可以通过[`themeConfig.sidebar`](/config/theme-configs#sidebar)来定义它.

```js
export default {
  themeConfig: {
    sidebar: [
      {
        text: 'Guide',
        items: [
          { text: 'Introduction', link: '/introduction' },
          { text: 'Getting Started', link: '/getting-started' },
          ...
        ]
      }
    ]
  }
}
```

## 基础的侧边栏

侧边栏菜单的最简单形式是传入一个链接组。第一级`item`定义侧边栏的一部分。它应该包含该部分的标题和实际指向该部分内容的路径。

```js
export default {
  themeConfig: {
    sidebar: [
      {
        text: 'Section Title A',
        items: [
          { text: 'Item A', link: '/item-a' },
          { text: 'Item B', link: '/item-b' },
          ...
        ]
      },
      {
        text: 'Section Title B',
        items: [
          { text: 'Item C', link: '/item-c' },
          { text: 'Item D', link: '/item-d' },
          ...
        ]
      }
    ]
  }
}
```

每个 `link` 都应当以 `/`开头. 如果在路径末尾加`/` 则表示该路径下的`index.md` 文件.

```js
export default {
  themeConfig: {
    sidebar: [
      {
        text: 'Guide',
        items: [
          // 这里`/guide/index.md`是/guide目录下的index.md文件.
          { text: 'Introduction', link: '/guide/' }
        ]
      }
    ]
  }
}
```

你最多可以定义六级套娃，超过六级将不显示。

```js
export default {
  themeConfig: {
    sidebar: [
      {
        text: 'Level 1',
        items: [
          {
            text: 'Level 2',
            items: [
              {
                text: 'Level 3',
                items: [
                  ...
                ]
              }
            ]
          }
        ]
      }
    ]
  }
}
```

## 多个侧边栏

您可能会根据页面路径显示不同的侧边栏。例如，如本网站所示，您可能希望在文档中创建单独的内容部分，例如"指南" 页面和 "配置" 页面.

将你的页面放到所需目录中

```
.
├─ guide/
│  ├─ index.md
│  ├─ one.md
│  └─ two.md
└─ config/
   ├─ index.md
   ├─ three.md
   └─ four.md
```

然后，更新您的配置文件。

```js
export default {
  themeConfig: {
    sidebar: {
      // This sidebar gets displayed when a user
      // is on `guide` directory.
      '/guide/': [
        {
          text: 'Guide',
          items: [
            { text: 'Index', link: '/guide/' },
            { text: 'One', link: '/guide/one' },
            { text: 'Two', link: '/guide/two' }
          ]
        }
      ],

      // This sidebar gets displayed when a user
      // is on `config` directory.
      '/config/': [
        {
          text: 'Config',
          items: [
            { text: 'Index', link: '/config/' },
            { text: 'Three', link: '/config/three' },
            { text: 'Four', link: '/config/four' }
          ]
        }
      ]
    }
  }
}
```

## 可折叠侧边栏

通过将 `collapsed` 选项添加到侧边栏组，它会显示一个切换按钮来隐藏/显示每个部分。

```js
export default {
  themeConfig: {
    sidebar: [
      {
        text: 'Section Title A',
        collapsed: false,
        items: [...]
      }
    ]
  }
}
```

默认情况下，所有部分都是“打开”的。如果您希望它们在初始页面加载时“关闭”，请将`collapsed` 选项设置为 `true`.

```js
export default {
  themeConfig: {
    sidebar: [
      {
        text: 'Section Title A',
        collapsed: true,
        items: [...]
      }
    ]
  }
}
```
