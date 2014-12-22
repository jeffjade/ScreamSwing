# <font color='purple'> 编程语言简史 </font>

[转载:原文链接Here](http://it.deepinmind.com/%E5%85%B6%E5%AE%83/2014/11/09/programming-languages.html)

------
一个朋友在跟我一块吃午饭的时候问了我一个问题：现代编程语言的发展历程是什么样的，它是如何发展到现在这样的？
他觉得我应该能答得上来，但其实我只能说个大概。

我跟他提了下机器语言，以及人们为了简化它所做的努力，并逐渐发明了一些更抽象的语言，它们最终会被翻译成0和1。

但是:一个偶然的机会我看到了Crockford关于Javascript的一个分享，开篇的时候他讲的正是编程语言的发展史——尽管这主要
是关于JavaScript以及影响到它的那些语言——这比我讲的可要生动多了。
------

##穿孔卡
一些都得从穿孔卡开始说起——就是一张张打满了小洞的纸片（下面有图有真相）。

发明
美国宪法中要求，每10年就得进行一次人口普查。到了19世纪末期，人口增长的实在是太频繁了，以至于1880的人口普查历时8年才最终完成，当时还都是通过纸和笔来完成的。

1890年，Herman Hollerith被授命去解决这一问题，他最终使用了穿孔卡来存储数据，并用一台制表机（tabulating machine）来进行统计和排序。

数据是根据硬纸片上打孔的位置来进行编码的，排列的方式是我们现在所熟识的行列式，并可以通过机器来进行处理。

![穿孔卡](http://www.iknownothing.com/wp-content/uploads/2014/10/Hollerith_Punched_Card-1024x459.jpg)

这次人口普查只花了一年时间便完成了。

##IBM
1896年，Hollerith成立了制表机器公司，开始了自己的事业。他把自己的设备和卡片出售给大的保险公司，以及包括英国，意大利，德国，俄罗斯，澳大利亚，加拿大，法国，挪威，波多黎各，菲律宾等国在内的多国政府[参见Here](http://en.wikipedia.org/wiki/HermanHollerith#Inventionsand_businesses)。

他的公司后来跟别的公司进行了合并，并在1924年最终成为了国际商业机器公司。没错，它就是IBM。

##现代用途
穿孔卡被认为是将数据录入到机器的最便捷的一种方式。

IBM后来仍然在使用这套系统——它叫做单位记录管理（Unit Record Management）——并一直用到了70年代，当然了，这比Hollerith最初的设计要先进得多。

Hollerith的穿孔卡流传甚广。它很快便被改进成了更简单的行列组。

##80个字符的限制
确切来说是12行，80列。你可能看到过有80个字符这个限制，是的，这是因为一张卡片最大的字符数就是80个。

没错，这已经被淘汰了好几十年了，不过80个字符的这个限制仍然延用到了现在。
![80字符限制卡片](http://www.iknownothing.com/wp-content/uploads/2014/10/Blue-punch-card-front-horiz-1024x460.png)

这个卡片可以用来做许多事情。比如说，顾客不会直接收到帐单而是收到了一些卡片，他们将卡片仔细地打上孔后再和要付的款项一同返还给商家。公司收到这些后会再进行处理并确认这次交易。

记账机是可编程的，它应该可以算作是世界上第一台现代的计算机。

##大型机/分时时代
大型机是政府与企业用来运行关键任务的大型计算机。
![大型机]("http://www.iknownothing.com/wp-content/uploads/2014/10/IBM_704_mainframe.gif")
在PC机发明以前（50年代到70年代），人们能使用的计算机就只有大型机。

大型机非常昂贵且体型巨大，只有大型的企业以及一些大学才有。几乎每台机器都是独一无二的，跟别的大型机完全不同。一套完整的系统由多个单元组成，占的地方有一整间屋子那么大。

大型机将程序和数据存储在内存中。你得使用最原始的指令来编写程序。

##还是穿孔卡
我为什么一开始就讲到穿孔卡是有我的原因的:-)

你得将指令在一堆卡片上进行穿孔才能运行你的程序。作为程序员，你是没有自己的计算机的，你得将程序写在这些穿孔卡上（或者是纸上，当然得有人把它们转换成穿孔卡），然后把这些卡片交给一个操作员，他会负责把它们录入到大学或者公司的机器里。过几个小时你就可以回来了，操作员会把结果打印出来给你，当然了，也会把你的卡片还给你。

如果你漏掉了一个分号的话，你得先修复这个问题，然后等第二天再来。

幸运的是当这些都还是常态的时候我还没出生，不过我也明白了当一个程序员是得有多苦逼。

##分时系统
由于计算机的时间非常宝贵，这段时期分时系统是最常见的操作计算机的方式。

这意味着不同的人可以通过一个终端来接入到同一台大型机上去使用它的资源。你可以使用打字机进行编程，完成之后再把你的程序提交上来。

打字机非常慢，一秒只能打印10个字符。这意味着你对程序的输出得计算得非常精确。

只有当你提交了自己的作业时计算机才会执行你的程序，其它时间你都处于离线状态（未连接到大型机上）。

分时技术在60年代就已经出现了，直到70年代末期这仍是当时主流的编程方式。
![分时系统](http://www.iknownothing.com/wp-content/uploads/2014/10/ASR-33_at_CHM.agr_-1024x768.jpg)

##ASCII
说到字符集，当时只支持非常有限的一些字符——不支持重音字母（accented letter），因此只适合使用英语。

为什么错误又被称为BUG？
1889年，托马斯.爱迪生连续两天晚上都在折腾他的留声机，因为它突然就没法用了，还会发出蟋蟀或者臭虫（BUG）的声音。于是便有了关于这个疯狂的发明家的一个笑话，就是说如果他能把自己发明里的臭虫清理掉的话，就可以变得很有钱，这也是第一次有记载的使用BUG来命名缺陷的记录。
![bug](http://www.iknownothing.com/wp-content/uploads/2014/10/H96566k.jpg)

第二次世界大战中，Grace Hopper发现一台计算器无法工作了，后来发现是因为一个继电器里面有只飞蛾，她把这事给记录了下来，"这是第一个发现的真正的BUG"。

创新之源（mother of all demos）
1968年，Doug Engelbart展示了如下几样东西：

鼠标
超文本
屏幕显示
组件
视频会议
待办事项
这些想法并没有让他变得富有也没有立马流行起来。不过它们为Xerox PARC所做的研究奠定了基础，于是诞生了第一个GUI系统，随后它便被Apple Lisa，Macintosh，微软所采用并逐渐流行了起来。

##迷你/微型计算机
继大型机之后，微机开始登上了舞台。

最终微型计算机成为了主流。微机就是非常小型的终端也称为个人计算机（PC，尽管当时几乎还没人在用）。

我认为，70年代才开始有了真正的计算机。

微软
这应该是家喻户晓的了——微软最早以Altair 8800起家的——这是一台DIY的计算机——它上面支持编程语言，这对位于阿尔伯克基的MITS公司（微仪系统家用电子公司）而言多少显得有点价值。"Microsoft"的真正意思是“微型计算机软件”

- - - -
#编程语言简史
好吧，看起来程序员这行一开始并不好混啊。

不同的计算机工作的方式各不相同，不过相同的一点是它们都只认二进制代码。也就是说，0和1的序列。计算机采用这种方式是因为这和电子开关非常契合，关就是0，开就是1。计算机其实还挺笨的。

刚开始的时候，要想在计算机上编程你得能够理解它的语言。也就是说，你得用0和1来和它交流。很明显对人类而言这绝对是噩梦，计算机科学家花费了许多工夫来将它抽象得更简单一些，以方便大家来编写程序。

下面简略地介绍了一下一些语言的来龙去脉。

##机器代码
机器代码或者说机器语言就是计算机的CPU能直接执行的一系列指令。

每条指令都会执行一个特定的底层的任务。CPU所直接运行的程序就是由一系列这种指令所组成的。

数值型机器代码（不是汇编代码）可以看作是编译及汇编后的计算机程序的最底层的一种表示形式，也可以看作是一门原始的硬件相关的编程语言。

直接使用数值机器代码来编程程序当然也是可以的，不过你得一个个比特来维护并且要手动来计算数字地址和常量，这太枯燥了，并且非常容易出错。现在已经没人这么干了，除非是需要进行极端优化或者调试的时候。

[参考](http://en.wikipedia.org/wiki/Machinecode#Machinecode_instructions)

##汇编语言
汇编语言并不是机器代码，不过也差不多。它直接关系到底层的架构，因此也就是没有任何抽象。

可以通过汇编程序来将汇编语言翻译成机器代码。汇编程序是第一个发明出来的软件工具。

下面是一段代码：

```
MOV AL, 1h ; Load AL with immediate value 1
MOV CL, 2h ; Load CL with immediate value 2
MOV DL, 3h ; Load DL with immediate value 3
```
汇编程序早在50年代就已经出现了，因为它们并不需要太多的代码分析：大多数时候它们只是把指令翻译成对应的可执行的指令就好了。程序员需要像底层的机器或者架构一样来进行思考。

一些资源有限的电子设备仍然在使用汇编语言，由汇编语言的程序去加载高级语言以及相关的库（比如说，硬件固件）。

70年代和80年代间汇编语言非常流行。比如说，几乎所有的控制台游戏都使用汇编语言，因为可用的内存少到仅有几KB。最早的1984的Macintosh机上许多代码都是用汇编语言写的，因为这样比较节省资源。

##Fortran
它出现的时候，人们已经对高级编程语言（就是比汇编语言抽象程序更高的语言）进行了大量的研究了。

Fortran最早是在50年代由IBM所发明的。

这个时候，发明特定的编程语言是为了解决特定领域的问题的：Fortran的发明是用于科学计算的，它很快便成为了这一领域的主流语言，并在随后的50年间取得了大量的成就。

到目前为止，在高性能计算领域它还是最流行的编程语言之一，世界上最快的超级计算机的测试及排名的程序就是由它编写的（参见http://en.wikipedia.org/wiki/Fortran）。

Fortran开创了使用星号来进行乘法的惯例，现在几乎所有的语言都仍在沿用这一规。

Fortran程序是这样的：
```
Program Hello
Print *, "Hello World!"
End Program Hello
```
下面是一张包含了一个Fortran程序的穿孔卡：
![Fortran](http://www.iknownothing.com/wp-content/uploads/2014/10/1280px-FortranCardPROJ039.agr_-1024x491.jpg)

##COBOL
COBOL（COmmon Business-Oriented Language， 面向商业的通用语言）的设计目标是用于商业用途。它试图使得编程语言看上去更像是英语，这样编程人员和维护人员都能看得懂。

Grace Hopper 也是它的设计者之一（就是发现了“BUG”的那位女士），她还发明了一门类英语的数据处理语言FLOW-MATIC，要实现一门类英语的通用的业务开发语言，她绝对是不二人选。

下面是COBOL中一个"Hello World!"程序的例子：
```
IDENTIFICATION DIVISION.
PROGRAM-ID. HELLO-WORLD.
ENVIRONMENT DIVISION.       
DATA DIVISION.
PROCEDURE DIVISION.
MAIN.
    DISPLAY 'Hello, world.'.
    STOP RUN.
```
  
##BASIC
BASIC（初学者通用符号指令代码，Beginner’s All-purpose Symbolic Instruction Code）由John G. Kemeny与Thomas E.Kurtz于1964年在新罕布什尔州的达特茅斯学院所发明。

BASIC就是为了分时系统所设计的。它是简化版的Fortran，更容易进行编程。

它提供了一种非常聪明的按行号来编辑程序的方式，不仅编写程序的时候会用到，像GOTO行跳转这样的操作也会用到。

从70年代中期到80年代，微机上通常都安装有不同版本的BASIC，这通常都是随着机器的固件一起发布的，这样小企业，教授，业余爱好者，咨询师等都可以在他们买得起的计算机上定制软件。

BASIC孕育了许多不同的语言，包括Visual BASIC,很长一段时间内它都是世界上最流行的编程语言，它是微软从Microsoft BASIC中改进而来的。

下面是一个简单的BASIC程序（用GW-BASIC写的）：
```
10 INPUT "What is your name: ", U$
20 PRINT "Hello "; U$
30 INPUT "How many stars do you want: ", N
40 S$ = ""
50 FOR I = 1 TO N
60 S$ = S$ + "*"
70 NEXT I
80 PRINT S$
90 INPUT "Do you want more stars? ", A$
100 IF LEN(A$) = 0 THEN GOTO 90
110 A$ = LEFT$(A$, 1)
120 IF A$ = "Y" OR A$ = "y" THEN GOTO 30
130 PRINT "Goodbye "; U$
140 END
```

##ALGOL 60
ALGOL60（算法语言1960，ALGOrithmic Language 1960）是1960年在专业协会推动下所诞生的非常优秀且影响巨大的一门编程语言。

它从未流行过但是它引入了许多重要的概念，包括取消GOTO语句。

像BASIC这样的语言里会需要用到行间跳转，这样使得程序的可读性很差，写出来的程序也很容易出错。

ALGOL 60引入了结构体与块的概念：它使用BEGIN和END（当时还没有花括号呢），多亏了ALGOL 60才开始有了块的概念，而不用再使用GOTO语句了。

ALGOL的目标是通用性更强一些，以便科学计算和业务开发都能使用。

ALGOL程序是这样的：
```
procedure Absmax(a) Size:(n, m) Result:(y) Subscripts:(i, k);
    value n, m; array a; integer n, m, i, k; real y;
comment The absolute greatest element of the matrix a, of size n by m
is transferred to y, and the subscripts of this element to i and k;
begin integer p, q;
    y := 0; i := k := 1;
    for p:=1 step 1 until n do
    for q:=1 step 1 until m do
        if abs(a[p, q]) > y then
            begin y := abs(a[p, q]);
            i := p; k := q
            end
end Absmax
```

##Pascal
Pascal由Niklaus Wirth于1968到1969年间进行设计并于1970年公诸于世，它也受到了ALGOL语言的影响。

它一度非常流行，尽管最初仅是设计为一个教学工具，但很长一段时间内有不少人都用它来进行通用性的编程。

然而，它的模块化有所欠缺并有一些设计上的问题，使得这门语言编程起来比较困难。

上段代码吧：
```
while a <> b do  WriteLn('Waiting');
 
if a > b then WriteLn('Condition met')   {no semicolon allowed!}
           else WriteLn('Condition not met');
 
for i := 1 to 10 do  {no semicolon for single statements allowed!}
  WriteLn('Iteration: ', i);
 
repeat
  a := a + 1
until a = 10;
 
case i of
  0 : Write('zero');
  1 : Write('one');
  2 : Write('two');
  3,4,5,6,7,8,9,10: Write('?')
end;
```
（我仍记得14岁的时候在学校用Pascal编程的情形，简直酷毙了）。

B
B语言由贝尔实验室于1969年所发明。它的设计受到了Fortran和BCPL的影响。

B语言实际上就是去除了Thompson所认为的无用组件的BCPL系统，以便使得它能适合当时微机的内存容量。 [http://en.wikipedia.org/wiki/B_(programming_language) ](http://en.wikipedia.org/wiki/B_(programming_language))
B引入了+=操作符（尽管应该念成=+），以及自增/自减操作符(++和--)

```
printn(n,b) {
        extrn putchar;
        auto a;
 
        if (a=n/b) /* assignment, not test for equality */
                printn(a, b); /* recursive */
        putchar(n%b + '0');
}
```
C
C语言就是是B语言加上了Pascal里面的一些好的特性所组成的。它由Dennis Ritchie于1969年到1973年间在贝尔实验室所发明。

C语言应该是最重要的一门语言了。它获得了前所未有的成功。

除此之外，许多语言都是在C的基础上进行设计的，包括：

C++（1976）
Objective-C(1986)
Perl(1988)
Java(1991)
Python(1991)
JavaScript(1995)
PHP(1995)
C#(1999)
Go(2007)
等等

##Simula
挪威的仿真语言Simula I和Simula 67——从语法上来讲——是ALGOL 60的完整的超集。

它的影响非常深远。Simula以ALGOL 60为基础，并添加了对象的概念，因此它也被认为是第一门面向对象的编程语言。

Simula 67(于1967年发布)引入了对象，类，继承和子类的概念，同时还有虚函数，协程，以及离散事件模拟。

这还不止，它还引入了垃圾回收的特性。

它的程序是这样的：
```
Begin
   Class Glyph;
      Virtual: Procedure print Is Procedure print;
   Begin
   End;

   Glyph Class Char (c);
      Character c;
   Begin
      Procedure print;
        OutChar(c);
   End;

   Glyph Class Line (elements);
      Ref (Glyph) Array elements;
   Begin
      Procedure print;
      Begin
         Integer i;
         For i:= 1 Step 1 Until UpperBound (elements, 1) Do
            elements (i).print;
         OutImage;
      End;
   End;

   Ref (Glyph) rg;
   Ref (Glyph) Array rgs (1 : 4);

   ! Main program;
   rgs (1):- New Char ('A');
   rgs (2):- New Char ('b');
   rgs (3):- New Char ('b');
   rgs (4):- New Char ('a');
   rg:- New Line (rgs);
   rg.print;
End;
```

##Smalltalk
Simula对Alan Kay的影响极大——他曾经就职于Xerox PARC，并于1972年开始研发Smalltalk。

Smalltalk最初是设计给小孩用的。它在真实环境下做了充分的测试，并进行了数次重构。它历经了多次改版在首次发布8年后才最终面世。

Smalltalk是一门伟大的语言，它是第一个真正的现代面向对象编程语言。

由于它的语法很难掌握，因此它一直也没能流行起来。然而，它几乎对所有的现代编程语言都产生了影响。Objective-C, C++, Java, C#, Eiffel, 和Ruby基本上都是C和Smalltalk的混合体。

下面这个例子演示了Smalltalk版的控制结构：

```
result := a > b
    ifTrue:[ 'greater' ]
    ifFalse:[ 'less or equal' ]
```
   
##Self
这是Smalltalk所影响的又一门语言——它也是在Xerox PARC中研发的——它就是Self)。

Self的设计目标是为了提升性能。它以Smalltalk为原型，并去掉了其中类的概念，以便运行速度能更快。

它没有使用类的概念，而是用到了原型：Self允许对象可以不通过类而直接继承自其它对象。

你可能也猜到了，JavaScript正是受它所影响的语言之一。

Scheme
Scheme是基于Actor模型设计的。Actor模型最早是1973年提出的，刚出现的时候被认为是个很前卫的概念。它是LISP语言)的一门方言，LISP是MIT于1958年所设计的一门人工智能语言。

它包含尾递归，词法闭包，以及许多很酷的特性。

示例：

```
;; Calculation of Hofstadter's male and female sequences as a list of pairs
 
(define (hofstadter-male-female n)
  (letrec ((female (lambda (n)
             (if (= n 0)
             1
             (- n (male (female (- n 1)))))))
       (male (lambda (n)
           (if (= n 0)
               0
               (- n (female (male (- n 1))))))))
    (let loop ((i 0))
      (if (> i n)
      '()
      (cons (cons (female i)
              (male i))
        (loop (+ i 1)))))))
 
(hofstadter-male-female 8)
 
===> ((1 . 0) (1 . 0) (2 . 1) (2 . 2) (3 . 2) (3 . 3) (4 . 4) (5 . 4) (5 . 5))
```
#E语言
E语言揉合了Java与Joule，它是一门专为安全相关的应用程序所设计的语言。

它以Actor模型为基础，并实现了能力对象模型。

```E
def makeMint(name) :any {
   def [sealer, unsealer] := makeBrandPair(name)
   def mint {
     to makePurse(var balance :(int >= 0)) :any {
       def decr(amount :(0..balance)) :void {
         balance -= amount
       }
       def purse {
         to getBalance() :int { return balance }
         to sprout() :any { return mint.makePurse(0) }
         to getDecr() :any { return sealer.seal(decr) }
         to deposit(amount :int, src) :void {
           unsealer.unseal(src.getDecr())(amount)
           balance += amount
         }
       }
       return purse
     }
   }
   return mint
 }
```

##JavaScript
终于说到它了。

JavaScript已经成为了一门非常重要的语言。在能访问到网络的设备里总会出现它的身影，它是WEB平台的顶梁柱，也是绝大多数WEB应用及移动应用的基石。多亏了Node.js，它现在也活跃到了服务端开发中。

JavaScript是基于Java, Scheme与Self来设计的。

它最初是由Netscape公司开发的，原本是希望实现一套类似于苹果公司的HyperCard的东西——这是苹果公司的Macintosh与IIGS电脑上的一款应用程序以及编程工具，它可以使程序开发变得更为简单——Netscape把它集成到了浏览器里。

它的作者Brendan Eich希望基于Scheme来进行设计，但Netscape的管理层认为大家不喜欢Scheme的语法，并要求他将其设计得与Java更像一点。

JavaScript综合了Java的语法（要不就不叫JavaScript了），Scheme的函数模型，以及Self的原型的特性。

由于Netscape公司的推动，它仅花了两周时期便实现完成并发布了出来。
- - - -