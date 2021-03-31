# Flutter介绍
## Flutter简介
Flutter是一个由谷歌开发的开源移动应用软件开发工具包，用于为Android、iOS、Windows、Mac、Linux、Google Fuchsia开发应用。Flutter第一个版本支持Android操作系统，开发代号称作“Sky”。 它于2015年4月的Flutter开发者会议上被公布，宣称其目标为实现120FPS的渲染性能。在上海Google Developer Days的主题演讲中，Google宣布了Flutter Release Preview 2，这是Flutter 1.0之前的最后一个重要版本。2018年12月4日，Flutter 1.0在Flutter Live活动中发布，是该框架的第一个“稳定”版本。2019年12月11日，在Flutter Interactive活动上发布了Flutter 1.12，宣布Flutter是第一个为环境计算设计的UI平台。  
***
## Flutter的优势
- 文档丰富，快速入手
相比其他的开发方案，Flutter提高了大量的文档，能够非常快速且友好的让你掌握Flutter技术
- 系统可定制性强  
  Flutter并不只是WebView，也可以解释JS后操作系统的原声控件，Flutter核心只有一层轻量的C和C++代码，Flutter在Dart中实现了其他大部分系统(组合，手势，动画，框架，widget等)，因此，这意味着开发人员可以轻易的进行读取，更改，替换或移除等操作。这为开发人员提供了对系统的巨大可定制性。

- 性能高  
  采用JIT模式，避免了每次改动都要进行编译，极大的节省了开发时间。同时也基于AOT发布包，在发布时可以通过AOT生成高效的ARM代码以保证应用性能，而JavaScript则不具备该性能。

- 创建美观，高度定制的用户体验。  
  受益于使用Flutter框架提供的丰富的Material Design和Cupertino（iOS风格）的widget
  实现定制，美观，品牌驱动的设计，而不受原生控件的限制。
***
## 核心原则
Flutter包括一个现代的响应式框架、一个2D渲染引擎、现成的widget和开发工具。这些组件可以帮助您快速地设计、构建、测试和调试应用程序。

一切皆为widget
Widget是Flutter应用程序用户界面的基本构建块。每个Widget都是用户界面一部分的不可变声明。 与其他将视图、控制器、布局和其他属性分离的框架不同，Flutter具有一致的统一对象模型：widget。

Widget可以被定义为:

一个结构元素（如按钮或菜单）
一个文本样式元素（如字体或颜色方案）
布局的一个方面（如填充）
等等…
Widget根据布局形成一个层次结构。每个widget嵌入其中，并继承其父项的属性。没有单独的“应用程序”对象，相反，根widget扮演着这个角色。

您可以通过告诉框架使用另一个widget替换层次结构中的widget来响应事件，例如用户交互，替换后框架会比较新的和旧的widget，并高效地更新用户界面。

组合 > 集成
Widget本身通常由许多更小的、单一用途widget组成，这些widget结合起来产生强大的效果。例如，Container是一个常用的widget， 由多个widget组成，这些widget负责布局、绘制、定位和调整大小。具体来说，Container由 LimitedBox、 ConstrainedBox、 Align、 Padding、 DecoratedBox、 和Transform组成。 您可以用各种方式组合这些以及其他简单的widget，而不是继承容器。

类层次结构很浅且很宽，可以最大限度地增加可能的组合数量。  

![11](/Users/tanglu/SOFT0047-mobile-development/lab1/1.png)

您还可以通过与其他widget组合来控制widget的布局。例如，要将widget居中，可以将其封装在Center widget中。有填充、对齐、行、列和网格的widget。 这些布局widget没有自己的可视化表示。相反，他们唯一的目的是控制另一个widget布局的某些方面。要理解widget以某种方式呈现的原因，检查相邻widget通常很有帮助。

分层的框架
Flutter框架是一个分层的结构，每个层都建立在前一层之上。


该图显示了框架的上层，它比下层的使用频率更高。有关构成Flutter分层框架的完整库，请参阅我们的API文档。

这个设计的目标是帮助你用更少的代码做更多的事情。例如，Material层是通过组合来自Widget层的基本Widget来构建的， 并且Widgets层本身是通过较低级对象渲染层构建的。

层为构建应用程序提供了许多选项。选择一种自定义的方法来释放框架的全部表现力，或者使用构件层中的构建块，或混合搭配。 您可以实现Flutter提供的所有现成的widget，或者使用Flutter团队用于构建框架的相同工具和技术创建您自己的定制widget。

没有什么是隐藏的。您可以从高层次，统一的widget概念中获得开发效率优势，而不会牺牲您希望深入到下层的能力。

构建widget
您可以通过实现widget的build返回widget树（或层次结构）来定义widget的独特特征 。 这棵树更具体地表示了用户界面的widget层次。例如，工具栏widget的build函数可能返回一个包含一些文本和各种按钮的水平布局。 然后，框架递归地构建widget，直到该所有widget构建完成，然后framework将他们一起添加到树中。

widget的构建函数一般没有副作用。每当它被要求构建时，widget应该返回一个新的widget树，无论widget以前返回的是什么。 Framework会将之前的构建与当前构建进行比较并确定需要对用户界面进行哪些修改。

这种自动比较非常有效，可以实现高性能的交互式应用程序。而构建函数的设计则着重于声明widget是由什么构成的，而不是将用户界面从一个状态更新到另一个状态的(这很复杂性)，从而简化了代码。

处理用户交互
如果widget需要根据用户交互或其他因素进行更改，则该widget是有状态的。例如，如果一个widget的计数器在用户点击一个按钮时递增，那么该计数器的值就是该widget的状态。 当该值发生变化时，需要重新构建widget以更新UI。

这些widget将继承StatefulWidget（而不是State）并将它们的可变状态存储在State的子类中。


每当你改变一个State对象时（例如增加计数器），你必须调用setState()来通知框架，框架会再次调用State的构建方法来更新用户界面。 有关管理状态的示例，请参阅创建新Flutter项目时的MyApp 模板 。

有了独立的状态和widget对象，其他widget可以以同样的方式处理无状态和有状态的widget，而不必担心丢失状态。 父widget可以自由地创造子widget的新实例且不会失去子widget的状态，而不是通过持有子widget来维持其状态。 框架在适当的时候完成查找和重用现有状态对象的所有工作。

