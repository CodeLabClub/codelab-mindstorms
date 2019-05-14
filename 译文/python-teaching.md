# 为什么Python对于基础编程课程中的初学者来说是一门很棒的语言。

> Author: May 2007 ([Philip Guo](http://pgbovine.net/philip-guo-cv.pdf))

> Translator: May 2019 ([郭瑞彪](https://github.com/guoruibiao))


这篇文章代表了我为什么觉得`Python`对于教授学生关于计算机编程是很棒的初学语言（对基础编程课程更多的观点可以查看[这篇文章](http://pgbovine.net/prog-curriculum.htm)）。我已经从我从事的初学者`Python`教学中提炼出了一些心得。

简单地说，我所有的判断，断言强化了我的信念，那就是大部分的编程语言初学者并不在乎计算机科学或者编程语言理论，却简单地想着通过尽可能少的模板代码让计算机去执行。他们需要写的代码越少，可能出现的错误和漏洞也就越少，他们也就更少地被困惑甚至放弃编程。

我认为`Python`相比于其他编程语言来说算是一门更偏上级的语言，因为它让学生把注意力更少得集中在比如类型，编译器，模板代码或者演算相关任务的算法，数据结构这种细节性的知识上（类似的语言还有`Ruby`），下面我列举一些对初学者来说让它变得好用的特色：

## 无需声明变量类型
当一个学生刚开始学类似于`C++`或者`Java`这种静态类型的语言时，通常他/她写的第一行代码便是声明像`int count`或者`List<String> seq`这种变量声明。这些代码除了充当视觉混乱和模糊执行真实动作的语句之外，什么也不做.在这些小型的程序中，初学者甚至要声明占据总代码行数`1/4`到`1/3`的变量，而编程老手认为声明变量和类型不是头等大事，但是他们会很厌恶让编译器因为类型问题而报错的代码。（在某些静态类型编程语言中你也可以不必声明类型，比如`ML`和其他有类型推断的语言，但是第一次就教学生`ML`语言就像是给人家鼻子上狠狠来了一捶）。

## 运行期类型错误而不是编译期类型错误
编译时类型错误永远困扰着学生。至少让代码先跑起来，做点什么，这比连编译都通过不了，什么也不做要强点。在生产环境中，带有严格的类型检查是非常重要的，因为这样可以大大降低因为运行期类型错误导致的事故，但是学生又不会去写核反应堆的核心代码，他们只是要写一些一二十行的玩具代码。至少让他们的程序跑起来，让他们知道在运行期，哪一行代码出了错。虽然有些错误可能会隐藏的很深，而且需要学生对源代码的错误有很敏感的认知。但是瑕不掩瑜，先让代码跑起来~

对于一个编程新手来说，最打击士气的莫过于你想让代码按照你的意愿去执行，却被一个叫编译器的神秘暴君告知拒绝把你的代码转换成可执行程序。理想状态下，学生越频繁地运行他们的代码，他们就越能缩短在编程期间的编辑-调试的迭代周期，也就越有动力学下去。

布鲁斯·埃凯尔的[强类型与强测试](http://www.mindview.net/WebLog/log-0025)文章中讨论了动态类型语言在生成高质量代码方面的优势，即使是资深程序员来说也是如此。

## `print`语句是多态的，会自动插入空格与换行
新手会在程序输出与调试代码中大量使用`print`语句，毕竟第一天就教他们如何使用`Python`的调试器会有点困难。不像`C`风格中`printf`的语法，Python的`print`可以正确地打印出所有类型的变量，而无需考虑是基础变量还是复合变量。相比于下面的让人发狂的代码：
```
printf("%s lives at %d %s\n",
       person, street_number, street_name);
```
学生可以写出如下更清晰明智的代码：
```
print person, "lives at", street_number, street_name
```
上面的`Python print`语句实际上看起来应该打印出一行，看起来像“约翰·多伊住在榆树街135号”，而`C printf`版本看起来只适合于，嗯，`C`程序员。

## 字符串，列表，字典内置，且使用统一的语法操作
即时作为初级程序员，你也可以通过使用字符串（存储文本数据），列表（存储序列数据），字典（存储关联数据）写出很棒的代码。Python通过统一的操作语法让这三个基础的数据结构变得极其容易操作， 比如：使用`[...]`进行元素访问，使用`for ... in ...`来循环迭代，使用`if ... in ...`来做成员测试。

动态类型使得避免列表，字典的长类型声明变得更加容易，比如某些难看的`Map<String, List<Integer>>`, 而使用简单的初始化像`x = [1, 2, 3]`就可以避免重复地调用方法去填充这些值。例如你想创建一个`key`为字符串类型，`value`为数值型列表的字典，只需要把对应的内容扔进去就好，而不需要做冗长的声明。
```python
d = {}
d["my bowling scores"] = [120, 140, 165]
```
而实现相同的初始化功能，`Java1.5`的代码却是这样的：
```java
Map<String, List<Integer>> d = new HashMap<String, List<Integer>>();
List<Integer> lst = new LinkedList<Integer>();
lst.add(120);
lst.add(140);
lst.add(165);
d.put("my bowling scores", lst);
```
我不反对`Java`（可怜的`Java`总是会被拿出来抨击），但是我的天呐，看看这一堆冗长的代码，把相同的数据填到字典中却需要多敲多少次键盘。

好吧，好吧，我知道对于一个大项目中工作经验丰富的程序员来讲，多输入几个单词无关紧要，但对于初学者呢？想想哪一个版本的代码更容易被理解！我不敢想象一个初学者要怎样去理解这一段`Java`代码。初学者不关心类型声明，`Java`泛型，参数多态机制或者其他奇怪的编程术语，他们只想着用尽可能少的代码去实现自己预期的想法。

## 漂亮、干净的语法，足够简洁，不会产生视觉混乱，但不要太简洁，以免造成混乱
毫无疑问`Python`代码看起来优雅，干净，容易书写易读易理解。但是，`Python`代码不太简洁，容易混淆，比如许多`Perl`代码经常会出现的情况。它在简洁和清楚两个层次上做了很好的平衡。

最初`Python`吸引我的地方是我发现写`Python`代码很有趣，因为它看起来很美观。虽然这听起来有一点老套，但是看`Python`代码时唤起的愉快的发自内心的情感可以提高程序员的工作效率，让他/她觉得代码更整洁，更容易理解。如果你需要每天长时间盯着代码好几个小时，那么它越看起来越优雅就越好（世界上大部分事情都是如此）。

## 交互式命令提示符和无需重启交互式会话即可动态重新加载模块的能力
无论何时一个编程语言初学者有关于一个函数或者语言特色是如何工作的问题时，最好是使用科学的方法来进行回答，那就是**先去试试看看发生了什么**，然后再去改善，润色自己的理解，再去重新实验。最佳实践就是通过交互式命令提示，因为不需要保存源文件，重新编译它，重新编辑来消除你刚刚修改的代码中愚蠢的类型错误，重新编译，然后重新执行。使用`Python`，你可以在交互式提示中创建数据结构，并实时测试它们。

更好的是，当你想去测试写在源文件（`Python`中称之为模块）的函数，你可以使用`reload`函数来重新加载你的改动而无需退出交互式环境。这对于在运行试验模块前需要做很多准备工作的场景十分的有帮助。一个快速的编辑-调试周期会使学生受益颇多，因为这会让他们感觉测试起代码来更自由，代价更低。实验的越多，理解的越深，越有学下去的动力。

## 返回新值而不是改变现有对象的函数操作
`Python`标准库的许多操作都是以函数式风格编写的，这意味着这些操作会返回新值而不是修改原来的对象。在教授学生使用`Python`的交互式命令提示符时，我发现这个函数性质非常有用，因为它允许人们在不改变原对象的情况下继续对同一对象进行重复实验。

例如，当我教授学生关于字符串切片的内容（目标是去除字符串两边的双引号）时，我创建了一个值为`"Weight in kilograms"`的`x`字符串类型变量，为了演示字符串切片的语法，我让他们尝试用不同的索引切片，以便自己查看结果。
```python
>>> print x
"Weight in kilograms"
>>> print x[1:]
Weight in kilograms"
>>> print x[2:]
eight in kilograms"
>>> print x[3:]
ight in kilograms"
>>> print x[:-1]
"Weight in kilograms
>>> print x[:-2]
"Weight in kilogram
>>> print x[:-3]
"Weight in kilogra
>>> print x[1:-1]
Weight in kilograms
```
最后一行代码实现了去除首部和尾部双引号的需求，因为切片操作每次返回的都是新值，而原始的字符串并没有被改变，所以可以被无限次操作而不受影响。试想如果不是这样，测试切片操作时每次都需要重新修改原始字符串的内容，这会是多么的不方便。

对初学者来说最佳实践就是去不断做实验，而函数式风格对此有很大的促进作用。

## 全面的标准库以及大量可用的免费第三方库
大多数的介绍性编程课程都会让学生编写一些数学相关的程序，如计算菲波那切数列或者求素数，写一个四则运算计算器，求一个集合的平均数，因为这些都很容易实现而且不需要外部依赖。（毕竟，数学运算符在大多数编程语言中是原始运算，因为它们在大多数机器语言中是原始运算）

我个人认为如果学生脑海里有现实生活中应用的需求，那么编程将变得更加有趣，例如[用脚本管理自己的电子照片](http://pgbovine.net/xml_gal_manual.htm)，给他们最喜欢的聊天客户端写拓展，互联网图片爬虫等。这些应用会使用到大量的库，幸运的是，`Python`中有很多这样的库。没有这些库的帮助，学生永远也不能跳出编写玩具程序的范畴，更别提去创造能激励他们进一步学习的有用的软件了。

## 操作符被重载到合适的程度
操作符重载可以是代码看起来更简洁易读，但是滥用也会使代码变得一团糟。对一个编程语言来说允许操作符重载的程度（以及标准库中哪些运算符实际重载)，就决定了代码的可读性。一种极端是，在`C`和`Java`中，几乎没有操作符被重载。所以为了实现大部分的操作会调用繁多的函数/方法。另一种极端是，`Perl`中大部分操作符都被重载了，在不同的上下文中有不同的含义，这使得代码看起来一团糟。我个人觉得`Python`在操作符重载方面取得了一个很好的平衡，比如`+`和`[]`。

举例来讲，`+`操作符是演示优雅的操作符重载的绝佳例子：数值加法，字符串，列表和元组的拼接等。如果你问初学者他们期望`+`为上述类型做什么，他们很容易猜出正确的功能。另一方面，如果你问初学者他们期望`+`对两个字典做些什么，他们就会感到困惑了，因为现实中没有特别直观的对两个字典进行合并的场景。或许你能将两个字典合并成一个更大的字典，但是当两个字点都包含某几个`key`时，保留哪一个呢？字典中`+`缺乏明确的含义，这可能是为什么它在这种类型上不会过载的原因。

---
reference links
<ul>
<li><a href="PG-Podcast-45-Kathleen-Tuite.htm">PG Podcast - Episode 45 - Kathleen Tuite on fostering technical communities and learning in public</a></li>
<li><a href="PG-Vlog-240-prototyping-with-code-4.htm">PG Vlog #240 - prototyping with code 4 (teaching software prototyping)</a></li>
<li><a href="debugger-culture-paper.htm">The Impact of Culture on Learner Behavior in Visual Debuggers</a></li>
<li><a href="PG-Podcast-40-Andy-Zhang.htm">PG Podcast - Episode 40 - Andy Zhang on building a university class profile</a></li>
<li><a href="learning-programming-at-scale-2018-talk.htm">Learning Programming at Scale</a></li>
<li><a href="conversational-programmer-papers.htm">Conversational Programmers: The Trilogy</a></li>
<li><a href="PG-Vlog-139-college-non-classroom-learning.htm">PG Vlog #139 - Learning in College ... Outside the Classroom</a></li>
<li><a href="non-native-english-speakers-learning-programming-paper.htm">Non-Native English Speakers Learning Computer Programming: Barriers, Desires, and Design Opportunities</a></li>
<li><a href="how-i-learned-programming.htm">How I Learned Programming</a></li>
<li><a href="PG-Vlog-74-python-tutor-live-help.htm">PG Vlog #74 - Get Live Help on pythontutor.com</a></li>
<li><a href="happyface-paper.htm">HappyFace: Identifying and Predicting Frustrating Obstacles for Learning Programming at Scale</a></li>
<li><a href="omnicode-paper.htm">Omnicode: A Novice-Oriented Live Programming Environment with Always-On Run-Time Value Visualizations</a></li>
<li><a href="PG-Vlog-51-word-choice.htm">PG Vlog #51 - Word Choice</a></li>
<li><a href="hackathon-paper.htm">Hack.edu: Examining How College Hackathons Are Perceived By Student Attendees and Non-Attendees</a></li>
<li><a href="PG-Vlog-39-learning-programming-at-scale.htm">PG Vlog #39 - Learning Programming at Scale</a></li>
<li><a href="learning-programming-at-scale-CACM.htm">Learning Programming at Scale (CACM)</a></li>
<li><a href="making-programming-accessible-for-all.htm">Making Programming Accessible for All (MIT alumni profile)</a></li>
<li><a href="older-adults-learning-programming-CACM.htm">Older Adults Learning Computer Programming (CACM summary)</a></li>
<li><a href="older-adults-learning-programming-paper.htm">Older Adults Learning Computer Programming: Motivations, Frustrations, and Design Opportunities</a></li>
<li><a href="older-adults-learning-programming.htm">Older Adults Learning Computer Programming (press release)</a></li>
<li><a href="PG-Podcast-21-Trey-Hunner.htm">PG Podcast - Episode 21 - Trey Hunner on teaching programming to working professionals</a></li>
<li><a href="PG-Podcast-13-Lindsey-Kuper.htm">PG Podcast - Episode 13 - Lindsey Kuper on a new kind of computing conference</a></li>
<li><a href="PG-Podcast-11-Brad-Miller.htm">PG Podcast - Episode 11 - Brad Miller on building long-lasting software in academia</a></li>
<li><a href="stackoverflow-barriers-paper.htm">Paradise Unplugged: Identifying Barriers for Female Participation on Stack Overflow</a></li>
<li><a href="python-tutor-history.htm">Python Tutor: The First Three Years</a></li>
<li><a href="learning-programming-at-scale-seminar-talk.htm">Interactive Systems for Learning Programming at Scale</a></li>
<li><a href="programming-forums-paper.htm">Toward a Domain-Specific Visual Discussion Forum for Learning Computer Programming: An Empirical Study of a Popular MOOC Forum</a></li>
<li><a href="learning-programming-at-scale.htm">Learning programming at scale</a></li>
<li><a href="codechella-codeopticon-codepourri-papers.htm">Codechella, Codeopticon, and Codepourri: The Trilogy</a></li>
<li><a href="cs-education-zoo-interview.htm">My CS Education Zoo interview</a></li>
<li><a href="teaching-web-programming.htm">My Basic Technology Stack for Teaching Web Programming</a></li>
<li><a href="programmers-talking-to-beginners.htm">Programmers: Please don't ever say this to beginners ...</a></li>
<li><a href="hello-world-c-python.htm">Hello World in C and Python</a></li>
<li><a href="CACM-python-most-popular-teaching-language.htm">Python is now the most popular introductory teaching language at top U.S. universities</a></li>
<li><a href="python-tutor-live.htm">Python Tutor Live</a></li>
<li><a href="tech-privilege-NPR-interview.htm">NPR Interview on Silent Technical Privilege</a></li>
<li><a href="unlocking-the-clubhouse-notes.htm">My book notes on Unlocking the Clubhouse</a></li>
<li><a href="tech-privilege.htm">Silent Technical Privilege</a></li>
<li><a href="CACM-hour-of-code.htm">Hour of Code: Observations from a Middle School Classroom</a></li>
<li><a href="ap-computer-science.htm">My Unexpectedly Awesome AP Computer Science Class</a></li>
<li><a href="hacker-school-residency.htm">Hacker School Residency</a></li>
<li><a href="teaching-librarians-programming.htm">Teaching Librarians Programming</a></li>
<li><a href="CACM-education-removes-fear.htm">Education Removes Fear: Some Examples From CS Courses</a></li>
<li><a href="programming-on-demand-2013-job-talk.htm">Programming On Demand: Wrangling, Iterating, and Opportunistic Learning</a></li>
<li><a href="CACM-teaching-real-world-programming.htm">Teaching Real-World Programming</a></li>
<li><a href="teaching-programming.htm">Teaching Programming To A Highly Motivated Beginner</a></li>
<li><a href="what-is-computer-science.htm">What is Computer Science? Efficiently Implementing Automated Abstractions</a></li>
<li><a href="prog-curriculum.htm">Introductory Computer Programming Education</a></li>
<li><a href="computer-science.htm">Computer Science in Modern Everyday Life</a></li>
<li><a href="6170-notes.htm">Java and Software Engineering Notes</a></li>
</ul>