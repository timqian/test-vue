想使用 OAuth 登录应用时，应用必须有一个服务器，用 code 与 secret 与 OAuth 服务器交换 token

## 大致过程：

1. 在 github 上见一个 application，设置 Homepage URL(homeUrl)， 和 Authorization callback URL(backUrl)
2. 用户访问 homeUrl 点击登录按钮，浏览器把用户转到 https://github.com/login/oauth/authorize, github 根据用户原先所在 url 知道了用户在使用那个 application, 如果用户同意该 app 的权限，github 会把用户转到 你原先填的 backUrl, 并带上一个code。**你自己的服务器** 用 code 和 你的 application 的secret id 向 github 换取 token。
3. 然后，app 就可以拿着这个 token 修改用户 github 上的内容了（如果用户一开始同意的话）

可以看出，想通过 OAuth2 得到 用户的 token，操作github 上内容。你自己必须有一个服务器来和 github OAuth 服务器通信。

所以，这种方式不适合我这个应用！！
