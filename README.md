# WebView APK Project

这是一个不用 Android Studio 的 Android WebView 壳项目。你把它上传到 GitHub，GitHub Actions 会自动生成可安装的 `app-debug.apk`。

## 这个项目做了什么

- 默认打开 `https://jable.tv/`
- 启用 JavaScript、Cookie、第三方 Cookie、DOM Storage
- 支持网页内返回键
- 支持网页视频全屏
- 顶部有细进度条
- `jable.tv` 之外的顶层跳转会交给系统浏览器处理
- 本机不需要安装 Android Studio

## 怎么生成 APK

1. 在 GitHub 新建一个空仓库。
2. 上传本文件夹里的所有文件，注意要让 `settings.gradle` 位于仓库根目录。
3. 打开仓库的 `Actions` 页面。
4. 选择 `Build Android APK`。
5. 点 `Run workflow`。
6. 构建完成后，在 workflow 页面底部的 `Artifacts` 下载 `webview-app-debug-apk`。
7. 解压后得到 `app-debug.apk`，传到安卓手机安装。

## 手机安装

手机一般需要开启：

```text
设置 -> 安全 -> 允许安装未知来源应用
```

不同品牌手机入口名称可能不一样。安装前请确认这个 APK 只用于你自己的设备和合法用途。

## 修改网站地址

编辑：

```text
app/src/main/res/values/strings.xml
```

改这一行：

```xml
<string name="start_url">https://jable.tv/</string>
```

如果要允许别的域名留在 App 内打开，也要改：

```text
app/src/main/java/com/codex/webviewwrapper/MainActivity.java
```

里面的：

```java
private static final String ALLOWED_HOST = "jable.tv";
```

## 修改 App 名称

编辑：

```text
app/src/main/res/values/strings.xml
```

改这一行：

```xml
<string name="app_name">WebView APK</string>
```

## 注意

- 这是 Debug APK，适合自己安装测试。
- 不建议公开分发或上架成人内容类 WebView App。
- 有些网站可能会限制 WebView、视频源、防盗链或登录环境，这不是 APK 本身一定能解决的。
- 不要用这个项目绕过网站登录、地区限制、版权限制或其他访问控制。
