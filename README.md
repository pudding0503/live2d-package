# Live2D 使用整合包

![build with love](https://forthebadge.com/images/badges/built-with-love.svg)
![](https://forthebadge.com/images/badges/uses-html.svg)
![](https://forthebadge.com/images/badges/made-with-javascript.svg)

## 整合包清单 🧾

想要建立自己的整个 Live2D 服务，需要以下项目清单：

1. Live2D API（用于搭建自己的 Live2D 后端，需要 PHP >= 5.2）
2. Live2D Widget（用于前端载入 Live2D 模型和服务）
3. Live2D Model（更多的 Live2D 模型）
4. Live2D Cubism（用于制作自己的 Live2D 模型）

## 使用方法 🔨

### 1. Live2D API

首先，需要搭建一个自己的 Live2D API。

> 仓库: https://github.com/fghrsh/live2d_api

#### 1.1 环境要求

- PHP 版本 >= 5.2（静态空间和对象存储不可用）
- 依赖 PHP 扩展：json

原仓库见上面的地址。我已将相关文件存在 `/live2d-api` 文件夹之中，直接将整个文件夹上传至 PHP 环境即可使用。

更多信息，如API接口的使用，模型的位置与增减等，详见 [Live2D API 说明](https://github.com/fghrsh/live2d_api/blob/master/README.md)。

### 2. Live2D Widget

Live2D Widget 是在前端载入 Live2D 模型的插件。

> 仓库: https://github.com/stevenjoezhang/live2d-widget

原仓库见上面的地址。我已将相关文件存在 `/live2d-widget` 文件夹之中：

```
+-autoload.js（载入模型的JS）
+-live2d.min.js（Live2D模型必要文件）
+-waifu-tips.js（语言文字交互的JS）
+-waifu-tips.json（额外补充的语言文字交互的JSON文件）
+-LICENSE（许可文件）
```

#### 2.1 使用方法

修改 `autoload.js` 文件第2行的目录为自己的插件路径。例如，此例示文件位于 `live2d-widget` 文件夹，则修改路径为：

```javascript
live2d_path = "/live2d-widget/";
```

并修改第35～36行 Live2D API 的路径自己搭建的路径：

```javascript
initWidget({
	waifuPath: live2d_path + "waifu-tips.json", //额外补充的语言文字交互的JSON文件
	apiPath: "https://live2d.fghrsh.net/api/", //自己搭建的Live2D API地址
});
```

最后，将 `autoload.js` 文件加入 `<head>` 或 `<body>`，即可展现出效果：

```html
<script src="autoload.js"></script>
```

#### 2.2 额外支持

Live2D Widget 需要 Font Awesome (v4 或 v5) 图标支持，请确保相关样式表已在页面中加载。

以 Font Awesome v4 为例，请在 `<head>` 中加入：

```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/font-awesome/css/font-awesome.min.css">
```

否则图标将无法正常显示。（如果网页中已经加载了任何版本的 Font Awesome，就不要重复加载了）

#### 2.3 语言文字修改

若要调整交互文字提示，修改 `waifu-tips.js` 与 `waifu-tips.json` 文件即可。

```
+-waifu-tips.js（语言文字交互的JS）
+-waifu-tips.json（额外补充的语言文字交互的JSON文件）
```

更多信息，详见 [Live2D Widget 说明](https://github.com/stevenjoezhang/live2d-widget/blob/master/README.md)。

### 3. Live2D Model

虽然 Live2D API 内置了一些模型，但是你仍可以添加额外的模型。

> 仓库: https://github.com/Eikanya/Live2d-model

模型使用方法，详见 [Live2D Model 说明](https://github.com/Eikanya/Live2d-model/blob/master/README.md)。

### 4. Live2D Cubism

Live2D Cubism 是制作和修改 Live2D 模型的工具。

Live2D 官方网站：

+ [https://www.live2d.com](https://www.live2d.com)
+ [https://live2d.github.io](https://live2d.github.io/)

### 一个例子 🌰

通过以上四部完成的 Live2D 前端展示的实例：[点此查看](https://pudding0503.github.io/live2d-package/demo.html)

### 许可证 License

API 内所有模型 版权均属于原作者，仅供研究学习，不得用于商业用途。