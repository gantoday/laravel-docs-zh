# 应用程序结构

- [介绍](#introduction)
- [根目录](#the-root-directory)
- [App 目录](#the-app-directory)
- [为应用程序配置命名空间](#namespacing-your-application)

<a name="introduction"></a>
## 介绍

默认的 Laravel 应用程序结构是为了提供一个良好的开始，无论是构建大型还是小型应用。当然，你可以依照喜好自由地组织应用程序。Laravel 几乎没有强加限制任何类的放置位置 - 只要 Composer 可以自动加载这些类即可。

<a name="the-root-directory"></a>
## 根目录

一个新安装的 Laravel 根目录包含许多个目录：

`app` 目录，如你所料，包含应用程序的核心代码。我们之后将会很快深入探讨这个目录的细节。

`bootstrap` 目录包含几个框架启动跟自动加载配置的文件。

`config` 目录，顾名思义，包含所有应用程序的配置文件。

`database` 目录包含你的数据库迁移与数据填充文件。

`public` 目录包含前面的控制器和你的资源文件 (图片、JavaScript、CSS，等等)。

`resources` 目录包含你的视图、原始的资源文件 (LESS、SASS、CoffeeScript) 和「语言」文件。

`storage` 目录包含编译后的 Blade 模板、基于文件的 session、文件缓存和其他框架产生的文件。

`tests` 目录包含你的自动化测试。

`vendor` 目录包含你的 Composer 依赖模块。

<a name="the-app-directory"></a>
## App 目录

 应用程序的「内容」存在于 `app` 目录中。默认情况下，这个目录在 `App` 命名空间下并通过 Composer 使用 [PSR-4 自动加载标准](https://github.com/PizzaLiu/PHP-FIG/blob/master/PSR-4-autoloader-cn.md) 自动加载。 **你可以使用 `app:name` Artisan 命令变更这个命名空间**.

`app` 目录附带许多个额外的目录，例如：`Console`、`Http` 和 `Providers`。考虑 `Console` 和 `Http` 目录用作提供 API 进入应用程序的「核心」。HTTP 协定和 CLI 都是跟应用程序交互的机制，但实际上并不包含应用程序逻辑。换句话说，它们是两种简单地发布命令给应用程序的方法。`Console` 目录包含你全部的 Artisan 命令，而 `Http` 目录包含你的控制器、过滤器和请求。

`Commands` 目录当然是用来放置应用程序的命令。命令代表可以被应用程序放到队列的任务，以及可以在当前请求生命周期内同步运行的任务。

`Events` 目录，如你所料，是用来放置事件类。当然，使用类来代表事件不是必须的；然而，如果你选择使用它们，这个目录将会是通过 Artisan 命令行创建它们时的默认位置。

`Handlers` 目录包含命令和事件的处理类。处理进程接收命令或事件，并针对该命令或事件执行逻辑。

`Services` 目录包含各种「辅助」服务，囊括应用程序需要的功能。例如，Laravel 引入的 `Registrar` 服务负责验证 并创建应用程序的新用户。其他的例子可能是服务跟外部 API、评价系统或甚至是跟从你的应用程序汇集数据的服务交互。

`Exceptions` 目录包含应用程序的异常处理进程，也是个处置应用程序抛出的任何异常的好地方。

> **注意：** 在 `app` 目录中的许多类可以用 Artisan 命令产生。要查看可以使用的命令，在终端机执行 `php artisan list make` 命令。

<a name="namespacing-your-application"></a>
## 为应用程序配置命名空间

如前面所提到的，默认的应用程序命名空间为 `App`；然而，你可以变更这个命名空间成跟应用程序的名称一样，这可以简单地通过 `app:name` Artisan 命令完成。例如：如果你的应用程序叫做「SocialNet」，你将会执行下面的命令：

	php artisan app:name SocialNet
