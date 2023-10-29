# 将微信读书划线和笔记同步到Notion


本项目通过 Github Action 每两个小时同步微信读书划线到 Notion。

预览效果：https://book.malinkang.com

> [!WARNING]  
> 请不要在Page里面添加自己的笔记，有新的笔记的时候会删除原笔记重新添加。


## 使用

1. star 本项目
2. fork 这个工程
3. 获取微信读书的 Cookie
    * 浏览器打开 https://weread.qq.com/
    * 微信扫码登录确认，提示没有权限忽略即可
    * 按F12进入开发者模式，依次点 Network -> Doc -> Headers-> cookie。复制 Cookie 字符串;
4. 获取 NotionToken
    * 浏览器打开 https://www.notion.so/my-integrations
    * 点击 New integration 输入 name 提交
    * 点击 show，然后 copy
5. 复制[这个Notion模板](https://www.notion.so/malinkang/517ada8ea6534ae0afeb0b9e23d5554c?v=bdc3188f8fc04af5965293e53064722c&pvs=4)，删掉所有的数据，并点击右上角设置，Connections添加你创建的Integration。

6. 获取 NotionDatabaseID
    * 打开 Notion 数据库，点击右上角的 Share，然后点击 Copy link
    * 获取链接后比如 https://www.notion.so/malinkang/1b78f0fd0d03484caa00154285ffec0c?v=7ed7e3fbe69043a28d2847e76f075d99&pvs=4 中间的1b78f0fd0d03484caa00154285ffec0c就是 DatabaseID
7. 在 Github 的 Secrets 中添加以下变量
    * 打开你 fork 的工程，点击 Settings -> Secrets and variables -> New repository secret
    * 添加以下变量
        * WEREAD_COOKIE
        * NOTION_TOKEN
        * NOTION_DATABASE_ID
8. 在 Action 中创建新的 Action，并且 Run-All Action 选中当前项目

