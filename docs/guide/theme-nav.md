# 导航烂

导航栏是显示在页面顶部的导航栏。它包含站点标题、全局菜单链接等。

## 站点标题和LOGO

默认站点标题引用的是 [`config.title`](../config/app-configs#title) 的值. 如果你想自定义可以使用`themeConfig.siteTitle` 选项.

```js
export default {
  themeConfig: {
    siteTitle: 'My Custom Title'
  }
}
```

如果你的站点有LOGO,你可以通过图像路径来显示。你需要将logo图片放在`public` 文件夹 , 并定义它的绝对路径.

```js
export default {
  themeConfig: {
    logo: '/my-logo.svg'
  }
}
```

添加logo时，它会与站点标题一起显示。如果您只需要logo并且您想隐藏站点标题，请将siteTitle选项设置为false。

```js
export default {
  themeConfig: {
    logo: '/my-logo.svg',
    siteTitle: false
  }
}
```

你也可以为白天与黑暗模式定义不同的logo,详见[`themeConfig.logo`](../config/theme-configs#logo).

## 导航栏链接

你可以通过定义 `themeConfig.nav` 选项为你的导航栏添加链接.

```js
export default {
  themeConfig: {
    nav: [
      { text: 'Guide', link: '/guide' },
      { text: 'Configs', link: '/configs' },
      { text: 'Changelog', link: 'https://github.com/...' }
    ]
  }
}
```

这个 `text` 是在导航栏显示的文本,  `link` 是单击后指向的网址。 对于link关键字，其后跟的是`.md`以前的文件名, 不用包含`.md` 扩展名并且始终以 `/`开头.

导航栏也可以做成下拉菜单的样子，使用`item`关键字就可以啦！

```js
export default {
  themeConfig: {
    nav: [
      { text: 'Guide', link: '/guide' },
      {
        text: 'Dropdown Menu',
        items: [
          { text: 'Item A', link: '/item-1' },
          { text: 'Item B', link: '/item-2' },
          { text: 'Item C', link: '/item-3' }
        ]
      }
    ]
  }
}
```

Note that dropdown menu title (`Dropdown Menu` in the above example) can not have `link` property since it becomes a button to open dropdown dialog.

You may further add "sections" to the dropdown menu items as well by passing in more nested items.

```js
export default {
  themeConfig: {
    nav: [
      { text: 'Guide', link: '/guide' },
      {
        text: 'Dropdown Menu',
        items: [
          {
            // Title for the section.
            text: 'Section A Title',
            items: [
              { text: 'Section A Item A', link: '...' },
              { text: 'Section B Item B', link: '...' }
            ]
          }
        ]
      },
      {
        text: 'Dropdown Menu',
        items: [
          {
            // You may also omit the title.
            items: [
              { text: 'Section A Item A', link: '...' },
              { text: 'Section B Item B', link: '...' }
            ]
          }
        ]
      }
    ]
  }
}
```

### 定义链接活动状态

当前页面处于定义的`config`页面时，导航栏`Guide`会高亮显示，你可以定义需要在Guide下显示的路径

```js
export default {
  themeConfig: {
    nav: [
      // This link gets active state when the user is
      // on `/config/` path.
      {
        text: 'Guide',
        link: '/guide',
        activeMatch: '/config/'
      }
    ]
  }
}
```

::: warning
`activeMatch` is expected to be a regex string, but you must define it as a string. We can't use actual RegExp object here because it isn't serializable during the build time.
:::

## 社交链接

参阅 [`socialLinks`](../config/theme-configs#sociallinks)。
