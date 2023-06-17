## MVC、MVVM 模式的概念与区别

[查看](https://www.cnblogs.com/wenkangIT/p/15149077.html#:~:text=mvc%20%E5%92%8C%20mvvm%20%E5%85%B6%E5%AE%9E%E5%8C%BA%E5%88%AB%E5%B9%B6%E4%B8%8D%E5%A4%A7%E3%80%82,%E9%83%BD%E6%98%AF%E4%B8%80%E7%A7%8D%E8%AE%BE%E8%AE%A1%E6%80%9D%E6%83%B3%EF%BC%8C%E4%B8%BB%E8%A6%81%E5%8C%BA%E5%88%AB%E5%A6%82%E4%B8%8B%EF%BC%9A%202.mvvm%20%E9%80%9A%E8%BF%87%E6%95%B0%E6%8D%AE%E6%9D%A5%E9%A9%B1%E5%8A%A8%E8%A7%86%E5%9B%BE%E5%B1%82%E7%9A%84%E6%98%BE%E7%A4%BA%E8%80%8C%E4%B8%8D%E6%98%AF%E8%8A%82%E7%82%B9%E6%93%8D%E4%BD%9C%E3%80%82%203.mvc%E4%B8%ADModel%E5%92%8CView%E6%98%AF%E5%8F%AF%E4%BB%A5%E7%9B%B4%E6%8E%A5%E6%89%93%E4%BA%A4%E9%81%93%E7%9A%84%EF%BC%8C%E9%80%A0%E6%88%90Model%E5%B1%82%E5%92%8CView%E5%B1%82%E4%B9%8B%E9%97%B4%E7%9A%84%E8%80%A6%E5%90%88%E5%BA%A6%E9%AB%98%E3%80%82)

### MVC 框架

MVC 全名是 Model View Controller，是模型(model)－视图(view)－控制器(controller)的缩写，一种软件设计典范，用一种业务逻辑、数据、界面显示分离的方法组织代码，将业务逻辑聚集到一个部件里面，在改进和个性化定制界面及用户交互的同时，不需要重新编写业务逻辑。MVC 被独特的发展起来用于映射传统的输入、处理和输出功能在一个逻辑的图形化用户界面的结构中。

#### MVC 编程模式

MVC 是一种使用 MVC（Model View Controller 模型-视图-控制器）设计创建 Web 应用程序的模式： [1]

- Model（模型）表示应用程序核心（如数据库）。

- View（视图）显示效果（HTML 页面）。

- Controller（控制器）处理输入（业务逻辑）。

MVC 模式同时提供了对 HTML、CSS 和 JavaScript 的完全控制。

**Model（模型）**是应用程序中用于处理应用程序数据逻辑的部分。
　　通常模型对象负责在数据库中存取数据。

**View（视图）**是应用程序中处理数据显示的部分。
　　通常视图是依据模型数据创建的。

**Controller（控制器）**是应用程序中处理用户交互的部分。
　　通常控制器负责从视图读取数据，控制用户输入，并向模型发送数据。

### MVVM 框架

MVVM 是 Model-View-ViewModel 的简写。它本质上就是 MVC 的改进版。MVVM 就是将其中的 View 的状态和行为抽象化，让我们将视图 UI 和业务逻辑分开。当然这些事 ViewModel 已经帮我们做了，它可以取出 Model 的数据同时帮忙处理 View 中由于需要展示内容而涉及的业务逻辑。微软的 WPF 带来了新的技术体验，如 Silverlight、音频、视频、3D、动画……，这导致了软件 UI 层更加细节化、可定制化。同时，在技术层面，WPF 也带来了 诸如 Binding、Dependency Property、Routed Events、Command、DataTemplate、ControlTemplate 等新特性。MVVM（Model-View-ViewModel）框架的由来便是 MVP（Model-View-Presenter）模式与 WPF 结合的应用方式时发展演变过来的一种新型架构框架。它立足于原有 MVP 框架并且把 WPF 的新特性糅合进去，以应对客户日益复杂的需求变化。

#### MVVM 模式的组成部分

- 模型

模型是指代表真实状态内容的领域模型（面向对象），或指代表内容的数据访问层（以数据为中心）。

- 视图

  就像在 MVC 和 MVP 模式中一样，视图是用户在屏幕上看到的结构、布局和外观（UI）。

- 视图模型

  视图模型是暴露公共属性和命令的视图的抽象。MVVM 没有 MVC 模式的控制器，也没有 MVP 模式的 presenter，有的是一个绑定器。在视图模型中，绑定器在视图和数据绑定器之间进行通信。

- 绑定器

  声明性数据和命令绑定隐含在 MVVM 模式中。在 Microsoft 解决方案堆中，绑定器是一种名为 XAML 的标记语言。绑定器使开发人员免于被迫编写样板式逻辑来同步视图模型和视图。在微软的堆之外实现时，声明性数据绑定技术的出现是实现该模式的一个关键因素。

### MVVM 框架与 MVC 框架的区别

mvc 和 mvvm 其实区别并不大。都是一种设计思想，一种**软件架构模式**，主要区别如下：

1. mvc 中 Controller 演变成 mvvm 中的 viewModel

2. mvvm 通过数据来驱动视图层的显示而不是节点操作。

3. mvc 中 Model 和 View 是可以直接打交道的，造成 Model 层和 View 层之间的耦合度高。而 mvvm 中 Model 和 View 不直接交互，而是通过中间桥梁 ViewModel 来同步

4. mvvm 主要解决了:mvc 中大量的 DOM 操作使页面渲染性能降低，加载速度变慢，影响用户体验
