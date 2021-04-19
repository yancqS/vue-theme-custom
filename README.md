# vuepress-theme-modern-blog

基于z3by的[vuepress-theme-modern-blog](https://github.com/z3by/vuepress-theme-modern-blog)进行了一些自己的修改，因为并非对每个人都通用，所以没有提PR。为了使用方便，利于维护，因此单独发包。

然后对`vuepress-theme-modern-blog`开发者**z3by**表示感谢。

个人的`.vuepress/config.js`文件如下（可供参考，会更新）：

```js
module.exports = {
  title: 'Yoha\'s Blog',
  description: 'Blog is mainly used to record daily learning',
  markdown: {
    lineNumbers: true
  },
  head: [
    ['link', {
      rel: 'icon',
      href: `/favicon.ico`
    }]
  ],
  base: '/blog/',
  theme: "vuepress-theme-custom",
  summaryLength: 100,
  themeConfig: {
    translations: {
      read_more: 'Keep reading!',
      read_this_post: 'Read this post now!',
    },
    lastUpdated: 'Last Updated',
    cookies: {
      theme: 'dark-lime',
      buttonText: 'Got it!',
      message: 'We use cookies!',
    },
    summary: true,
    nav: [
      {
        text: 'Home',
        link: '/',
        icon: 'el-icon-house',
      },
      {
        text: 'Life',
        link: '/lifes/',
        icon: 'el-icon-lollipop',
      },
      {
        text: 'Handbook',
        link: '/handbooks/',
        icon: 'el-icon-s-management',
      },
    ],
    posts: {
      prepend: "Hi, I hope you'll <i>enjoy</i> this post!",
      append: "Hi, I hope you've <b>enjoyed</b> this post!",
    },
    about: {
      fullName: 'Qing',
      bio: 'xxxxxx',
      image: 'https://gitee.com/yancqS/blogImage/raw/master/blogImage/20201018002803.jpg',
    },
    logo: 'https://gitee.com/yancqS/blogImage/raw/master/blogImage/20210414163022.jpeg',
    friendlink: [
      {
        name: '阮一峰个人网站',
        link: 'http://www.ruanyifeng.com/home.html'
      },
    ],
    sitemap: true,
    footer: {
      contact: [
        {
          type: 'github',
          link: 'https://github.com/yancqs',
        },
        {
          type: 'weibo',
          link: 'https://weibo.com/superYoha',
        },
        {
          type: 'zhihu',
          link: 'https://www.zhihu.com/people/yoha-32-56',
        }
      ],
      copyright: [
        {
          text: 'Privacy Policy',
          link: 'https://policies.google.com/privacy?hl=en-US',
        },
        {
          text: `MIT Licensed Copyright © ${new Date().getFullYear()}-present`,
          link: '',
        },
      ],
    }
  },
  plugins: [
    'reading-progress',
    'vuepress-plugin-mathjax',
    [
      'vuepress-plugin-medium-zoom',
      {
        selector: '.content__default img',
        delay: 1000,
        options: {
          margin: 24,
          background: '#fff',
          scrollOffset: 0,
        },
      },
    ]
  ],
}
```