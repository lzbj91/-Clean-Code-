[TOC]
 
# 第1章 整洁代码
* **勒布朗法则**：Later equals never(稍候等于永不)  
* __单一权责原则__：Single Responsibility Principle(SRP)  
* **开放闭合原则**：Open Closed Principle(OCP)  
* **依赖倒置原则**：Dependency Inversion Principle(DIP)  
* ***

# 第2章 有意义的命名

## 2.2 名副其实
- [ ] *变量*、 _函数_ 或*类*的名称应该已经答复了所有的大问题；  
- [x] 选择***体现本意***的名称能让人更容易理解和修改的—___代码___。  
---

## 2.3 避免误导
1. 别用accountList来指称一组账号，除非它真的是List类型；  
2. 提防使用不同之处较小的名称；  
3. 慎用~~小写的l~~和~~大写的O~~。  
- - - 

## 2.4 做有意义的区分
> ==Variable==一词永远不应当出现在++变量名++中；  
==Table==一词永远不应当出现在表名中。
* * * 

## 2.5 使用读得出来的名称
> ==~~genymdhms~~==和==generationTimestamp==（生成时间戳）

## 2.6 使用可搜索的名称
> 单字母名称和数字常量有个问题，就是很难在一大篇文字中找出来。  
单字母名称仅用于短方法中的本地变量。  
名称长短应与其作用域大小相对应。

## 2.7 避免使用编码
> 把类型或作用域编进名称里面，徒然增加了解码的负担。

### 2.7.1 匈牙利语标记法
> Java程序员不需要类型编码。

### 2.7.2 成员前缀
> 不必用m_前缀来标明成员变量。

### 2.7.3 接口和实现
> ShapeFactory（接口）和ShapeFactoryImp（实现）。

## 2.8 避免思维映射
> 不应当让读者在脑中把你的名称翻译为他们熟知的名称。这种问题经常出现在选择是使用问题领域术语还是解决方案领域术语时。

## 2.9 类名
> 类名和对象名应该是==名词或名词短语==，如Customer、WIKIPage、Account和AddresParser。避免使用Manager、Processor、Data和Info这样的类名。类名不应当是~~动词~~。

## 2.10 方法名
> 方法名应当是==动词或动词短语==，如postPayment、deletePage或save。属性访问器、修改器和断言应该根据其值命名，并依==Javabean标准==加上get、set、is前缀。

## 2.11 别扮可爱
> 扮可爱的做法在代码中经常体现为使用俗语或俚语。

## 2.12 每个感念对应一个词
> 给每个抽象概念选一个词，并且一以贯之。例如：fetch、retrieve、get来给在多个类中的同种方法命名。

## 2.13 别用双关语
> 避免将同一单词用于不同目的。

## 2.14 使用解决方案领域名称
> 只有程序员才会读你的代码。尽管使用计算机科学（Computer Science，CS）术语、算法名、模式名、数学术语。

## 2.15 使用源自所涉及问题领域的名称
> 如果不能用程序员熟悉的术语来给手头的工作命名，就采用从所涉及问题领域而来的名称。至少，负责代码维护的程序员就能去请教领域专家了。

## 2.16 添加有意义的语境

## 2.17 不要添加没用的语境


# 第3章 函数

## 3.1 短小
> 函数的第一要则是短小。  
> 一屏

**代码块和缩进**  
> if语句、else语句、while语句等，其中的代码块应该只有一行。  

## 3.2 只做一件事
> 函数应该做一件事。做好这件事。只做这一件事。  
判断函数是否做了一件事，看是否能够再拆出一个函数。  

**函数中的区段**  
> 函数中的区段就是函数做太多事的征兆。

## 3.3 每个函数一个抽象层级
> 要确保函数只做一件事，函数中的语句都要在同一抽象层级上。  

**自顶向下读代码：向下规则**  
> 见本章末尾的代码

## 3.4 switch语句
> 确保每个switch都埋藏在较低的抽象层级，而且永远不重复。

## 3.5 使用描述性的名称
> 命名方式要保持一致。使用与模块名一脉相承的短语、名词和动词给函数命名。

## 3.6 函数参数
> 参数要少。

### 3.6.1 一元函数的普遍形式
> 问关于参数的问题、操作该参数、事件。

### 3.6.2 标识参数
> 向函数传入布尔值简直就是骇人听闻的做法。
### 3.6.3 二元函数
> 转为一元函数。

### 3.6.4 三元函数

### 3.6.5 参数对象
> 多个参数使用对象封装。

### 3.6.6 参数列表

### 3.6.7 动词和关键词
> 函数和参数应当形成一种良好的动词/名词对形式。

## 3.7 无副作用
**输出参数**  
> 使用report.appendFooter()（this）。

## 3.8 分隔指令与询问
> 函数要么做什么事，要么回答什么问题，单二者不可兼得。

## 3.9 使用异常替代返回错误码
> 返回错误码，就是在要求调用者立即处理错误。  
> 使用异常替代返回错误码，错误处理代码就能从主路代码中分离出来，得到简化。

### 3.9.1 抽离Try/Catch代码块
> 最好把try和catch代码块的主体部分分离出来，形成函数。

### 3.9.2 错误处理就是一件事

### 3.9.3 Error.java依赖磁铁
> 返回错误码通常暗示某处有个类或者枚举，定义了所有错误代码。  
```
    public enum Error {
        OK,
        INVALID,
        NO_SUCH,
        LOCKED,
        OUT_OF_RESOURCES,
        WAITING_FOR_EVENT;
    }
```
> 这样的类就是一块依赖磁铁，许多其他类需要使用他，当修改Error类时，所有其他类都要重新编译和部署。

## 3.10 别重复自己（Don't repeat yourself）
> 面向方面编程：Aspect Oriented Programming和面向组件编程：Component Oriented Programming

## 3.11 结构化编程
> 每个函数、函数中的代码块都应该有一个入口、一个出口，意味着每个函数中只该有一个return，循环中不能有break和continue语句，永远不能有goto语句。

## 3.12 如何写出这样的函数
> 不要一开始就使用这些规则，后期组装。
## 3.14 SetupTeardownIncluder程序
> SetupTeardownIncluder.java  

```
public class SetupTeardownIncluder {

	private PageData pageData;
	private boolean isSuite;
	private WiKiPage testPage;
	private StringBuffer newPageContent;
	private PageCrawler pageCrawler;
	
	public static String render(PageData pageData) throws Exception{
		return render(pageData,false);
	}
	
	public static String render(PageData pageData,boolean isSuite) throws Exception{
		return new SetupTeardownIncluder(pageData).render(isSuite);
	}
	

	private SetupTeardownIncluder(PageData pageData) {
		this.pageData = pageData;
		testPage = pageData.getWiKipage();
		pageCrawler = testPage.getPageCrawler();
		newPageContent = new StringBuffer();
	}
	
	private String render(boolean isSuite) throws Exception{
		this.isSuite = isSuite;
		if (isTestPage()) {
			includeSetupAndTeardownPages();
		}
		return pageData.getHtml();
	}
	
	private boolean isTestPage() throws Exception{
		return pageData.hasAttribute("Test");
	}
	
	private void includeSetupAndTeardownPages() throws Exception{
		includeSetupPages();
		includePageContent();
		includeTeardownPages();
		updatePageContent();
	}

	private void includeSetupPages() throws Exception{
		if (isSuite) {
			includeSuiteSetupPage();
		}
		includeSetupPage();
	}

	private void includeSuiteSetupPage() throws Exception{
		include(SuiteResponder.SUITE_SETUP_NAME,"-setup");
	}

	private void includeSetupPage() throws Exception{
		include("SetUp","-setup");
	}

	private void includePageContent() throws Exception{
		newPageContent.append(pageData.getContent());
	}

	private void includeTeardownPages() throws Exception{
		includTeardownPage();
		if (isSuite) {
			includeSuiteTeardownPage();
		}
	}

	private void includTeardownPage() throws Exception{
		include("TearDown","-teardown");
	}

	private void includeSuiteTeardownPage() throws Exception{
		include(SuiteResponder.SUITE_TEARDOWN_NAME,"-teardown");
	}

	private void updatePageContent() throws Exception{
		pageData.setContent(newPageContent.toString());
	}
	
	private void include(String pageName, String arg) throws Exception{
		WiKiPage inheritedPage = findInheritedPage(pageName);
		if (inheritedPage != null) {
			String pagePathName = getPathNameForPage(inheritedPage);
			buildIncludeDirective(pagePathName,arg);
		}
	}

	private WiKiPage findInheritedPage(String pageName) throws Exception{
		return PageCrawlerImpl.getInheritedPage(pageName,testPage);
	}

	private String getPathNameForPage(WiKiPage page) throws Exception{
		WiKiPagePath pagePath = pageCrawler.getFullPath(page);
		return PathParser.render(pagePath);
	}

	private void buildIncludeDirective(String pagePathName, String arg) {
			newPageContent.append("\n!include")
			.append(arg)
			.append(".")
			.append(pagePathName)
			.append("\n");
	}
	
	
}

```

# 第4章 注释
> 别给糟糕的代码加注释，重新写吧。

## 4.3 好注释
### 4.3.1 法律信息
### 4.3.2 提供信息的注释
### 4.3.3 对意图的解释
### 4.3.4 阐释
### 4.3.5 警示
### 4.3.6 TODO注释
### 4.3.7 放大

## 4.4 坏注释
### 4.4.1 喃喃自语
### 4.4.2 多余的注释
### 4.4.3 误导性的注释
### 4.4.4 循规式的注释
### 4.4.5 日志式的注释
### 4.4.6 废话注释
### 4.4.7 可怕的废话
### 4.4.8 能用函数或变量时就别用注释
### 4.4.9 位置标记
> // Actions /////////////////////////
### 4.4.10 括号后面的注释
### 4.4.11 归属与署名
### 4.4.12 注释掉的代码
### 4.4.13 HTML注释
### 4.4.14 非本地信息
### 4.4.15 信息过多
### 4.4.16 不明显的联系
### 4.4.17 函数头
### 4.4.18 非公共代码中的Javadoc
### 4.4.19 范例
> 修改前：

```
package com.disizhang.zhushi;

/**
 * @author Administrator
 *
 */
public class GeneratePrimes {

	/**
	 * @param maxValue is the generation limit.
	 * */
	public static int[] generatePrimes(int maxValue) {
		if (maxValue >= 2){ //the only valid case
			//ddeclarations
			int s = maxValue +1 ;// size of array
			boolean[] f = new boolean[s];
			int i;
			//initialize array to true.
			for ( i = 0;i < s;i++) {
				f[i] = true;
			}
			f[0] = f[1] = false;
			// sieve
			int j;
			for (i = 2;i < Math.sqrt(s) + 1; i++) {
				if (f[i]) { // if i is uncrossed , cross its multiples.
					for (j = 2 * i; j < s ;j += i) {
						f[j] = false; //multiple is not prime
					}
				}
			}
			
			// how many primes are there?
			int count = 0;
			for (i = 0;i < s; i++) {
				if (f[i]) {
					count ++; //bump count.
				}
			}
			
			int[] primes = new int[count];
			
			//move the primes into the result
			for (i = 0,j = 0;i < s;i++) {
				if (f[i]) {
					primes[j++] = i;
				}
			}
			return primes;
		}
		else { //maxValue < 2
			return new int[0]; // return null array if bad input.
		}
	}
}
```

> 修改后：

```
package com.disizhang.zhushi;

public class PrimeGenerator {
 
	private static boolean[] crossedOut;
	private static int[] result;
	
	public static int[] generatePrimes(int maxValue) {
		if (maxValue < 2) {
			return new int[0];
		}
		else {
			uncrossIntegersUpTo(maxValue);
			crossOutMultiples();
			putUncrossedIntegersIntoResult();
			return result;
		}
	}

	private static void putUncrossedIntegersIntoResult() {
		result = new int[numberOfUncrossedIntegers()];
		for (int j = 0, i = 2; i < crossedOut.length; i++) {
			if (notCrossed(i)) {
				result[j++] = i;
			}
		}
	}

	private static int numberOfUncrossedIntegers() {
		int count = 0;
		for (int i = 2; i < crossedOut.length; i++) {
			if (notCrossed(i)) {
				count++;
			}
		}
		return count;
	}

	private static void crossOutMultiples() {
		int limit = determinuIterationLimit();
		for (int i = 2;i <= limit; i++) {
			if (notCrossed(i)) {
				crossOutMultiplesOf(i);
			}
		}
	}

	private static void crossOutMultiplesOf(int i) {
		for (int multiple = 2 * i; multiple < crossedOut.length; multiple +=i) {
			crossedOut[multiple] = true;
		}
	}

	private static boolean notCrossed(int i) {
		return crossedOut[i] == false;
	}

	private static int determinuIterationLimit() {
		double iterationLimit = Math.sqrt(crossedOut.length);
		return (int)iterationLimit;
	}

	private static void uncrossIntegersUpTo(int maxValue) {
		crossedOut = new boolean[maxValue+1];
		for (int i = 2; i < crossedOut.length ; i++) {
			crossedOut[i] = false;
		}
	}
	
}
```

# 第5章 格式

## 5.1 格式的目的

> 代码关乎沟通是头等大事。

## 5.2 垂直格式
> 单个文件的尺寸（建议大多数200行，最多500行）

### 5.2.1 向报纸学习
> - 名称一目了然。
> - 源文件最顶部给舒高层次感念和算法。
> - 细节往下渐次展开。

### 5.2.2 概念间垂直方向上的间隔
> 使用空行增加可读性。

### 5.2.3 垂直方向上的靠近
> 紧密相关的代码应该互相靠近。

### 5.2.4 垂直距离
> - 变量声明：变量声明应尽可能靠近其使用的位置。循环中的控制变量应该总是在循环语句中声明。
> - 实体变量：应该在类的顶部声明。
> - 相关函数：调用者应该尽可能放在被调用者上面。
> - 概念相关：概念相关的代码应该放到一起。

### 5.2.5 垂直顺序
> 自上向下展示函数调用依赖顺序。

## 5.3 横向格式
> 横向120字符（上限）

### 5.3.1 水平方向上的区隔与靠近
> - 赋值操作符周围加上空格。
> - 函数名和左圆括号之间不加空格。
> - 加减运算符加空格，乘法不加。

### 5.3.2 水平对齐
> 多个变量声明不需要完全对齐。

### 5.3.3 对齐
> 类方法相对于类，方法的实现相对于方法的声明，代码块的实现相对于其容器代码块缩进一级。短小的if语句、while语句也需要缩进。

### 5.3.4 空范围

```
while(dis.read(buf, 0, readBufferSize != -1)) {}
```

## 5.4 团队规则
> 统一规则。

## 5.5 鲍勃大叔的格式规则

```
public class CodeAnalyzer implements JavaFileAnalysis{

	private int lineCount;
	private int maxLineWidth;
	private int widestLineNumber;
	private LineWidthHistogram lineWidthHistogram;
	private int totalChars;
	
	public CodeAnalyzer() {
		lineWidthHistogram = new LineWidthHistogram();
	}
	
	public static List<File> findJavaFiles(File parentDirectory) {
		List<File> files = new ArrayList<File>();
		findJavaFiles(parentDirectory,files);
		return files;
	}

	private static void findJavaFiles(File parentDirectory, List<File> files) {
		for (File file : parentDirectory.listFiles()) {
			if (file.getName().endsWith(".java")) {
				files.add(file);
			}
			else if (file.isDirectory()) {
				findJavaFiles(file,files);
			}
		}
	}
	
	public void analyzeFile(File javaFile) throws Exception{
		BufferedReader br = new BufferedReader(new FileReader(javaFile));
		String line;
		while ((line = br.readLine()) != null) {
			measureLine(line);
		}
	}

	private void measureLine(String line) {
		lineCount++;
		int lineSize = line.length();
		totalChars += lineSize;
		lineWidthHistogram.addLine(lineSize,lineCount);
		recordWideList(lineSize);
	}

	private void recordWideList(int lineSize) {
		if (lineSize > maxLineWidth) {
			maxLineWidth = lineSize;
			widestLineNumber = lineCount;
		}
	}
	
	public int getLineCount() {
		return lineCount;
	}
	
	public int getMaxLineWidth() {
		return maxLineWidth;
	}

	public int getWidestLineNumber() {
		return widestLineNumber;
	}

	public LineWidthHistogram getLineWidthHistogram() {
		return lineWidthHistogram;
	}
	
	public double getMeanLineWidth() {
		return (double) totalChars / lineCount;
	}
	
	public int getMedianLineWidth() {
		Integer[] sortedWidths = getSortedWidths();
		int cumulativeLineCount = 0;
		for (int width : sortedWidths) {
			cumulativeLineCount += lineCountForWidth(width);
			if (cumulativeLineCount > lineCount /2) {
				return width;
			}
		}
		throw new Error("Cannot get here");
	}

	private int lineCountForWidth(int width) {
		return lineWidthHistogram.getLinesforWidth(width).size();
	}
	
	private Integer[] getSortedWidths() {
		Set<Integer> widths = lineWidthHistogram.getWidths();
		Integer[] sortedWidths = (widths.toArray(new Integer[0]));
		Arrays.sort(sortedWidths);
		return sortedWidths;
	}
}
```

# 第6章 对象和数据结构
[跳到第2章](#第2章-有意义的命名)
## 6.1 数据抽象
> 具象点：暴露了实现

```
    public class Point {
        public double x;
        public double y;
    }
```

> 抽象点：暴露抽象接口

```
    public interface Point {
        double getX();
        double getY();
        void setCartesian(double x, double y);
        double getR();
        double getTheta();
        void setPolar(double r, double theta);
    }
```

> 具象机动车：

```
    public interface Vehicle {
        // 油箱容量以加仑计
        double getFuelTankCapacityInGallons();
        // 加仑的汽油
        double getGallonsOfGasoline();
    }
```

> 抽象机动车：

```
    public interface Vehicle {
        // 燃料剩余百分比
        double getPercentFuelRemaining();
    }
```

## 6.2 数据、对象的反对称性

> 过程式形状代码：

```
// 正方形
public calss Square {
    public Point toLeft;
    public double side;
}

// 矩形
public calss Rectangle {
    public Point toLeft;
    public double height;
    public double width;
}

// 圆
public calss Circle {
    public Point center;
    public double radius;
}

// 几何类
public class Geometry {

    public final double PI = 3.141592653589793;
    
    public double area(Object shape) throw NoSuchShapeException {
        if(shape instanceof Square) {
            Square s = (Square)shape;
            return s.side * s.side;
        } else if(shape instanceof Rectangle) {
            Rectangle r = (Rectangle)shape;
            return r.height * r.width;
        } else if(shape instanceof Circle) {
            Circle c = (Circle)shape;
            return PI * c.radius * c.radius;
        }
        // 添加一种新的形状，就要在此修改添加一种形状的面积计算方式
        throw new NoSuchShapeException();
    }
}
```

> 多态式形状：

```
// 正方形
public class Square implements Shape {
    private Point toLeft;
    private double side;
    
    public double area() {
        return side * side;
    }
}

// 矩形
public class Rectangle implements Shape {
    private Point toLeft;
    private double height;
    private double width;
    
    public double area() {
        return height * width;
    }
}

// 圆
public class Circle implements Shape {
    private Point center;
    private double radius;
    public final double PI = 3.1415926539793;
    
    public double area() {
        return PI * radius * radius;
    }
}

// 添加新的形状需要添加新的类
```

> 对象与数据结构之间的二分原理：  
> - 过程式代码（使用数据结构的代码）便于在不该懂既有数据结构的前提下添加新的函数，面向对象代码便于在不改动既有函数的前提下添加新类。  
> - 反过来讲：过程式代码难以添加新数据结构，因为必须修改所有函数。面向对象代码难以添加新的函数，因为必须修改所有类。  
> - 需要添加新数据类型而不是新函数的时候，对象和面向对象比较合适。想要添加新函数而不是数据类型的时候，过程式代码和数据结构更合适。

## 6.3 得墨忒耳定律(The Law of Demeter)

> 模块不应了解它所操作对象的内部情形。  
> 更准确的说，得墨忒耳定律认为，类C的方法f只应该调用一下对象的方法：  
> - C;  
> - 由f创建的对象;
> - 作为参数传递给f的对象;
> - 由C的实体变量持有的对象。  
方法不应调用由任何函数返回的对象方法。反例：

```
final String outputDir = ctxt.getOptions().getScratchDir().getAbsolutePath();
```

### 6.3.1 火车失事

> 切分：

```
Options opts = ctxt.getOptions();
File scratchDir = opts.getScratchDir();
final String outputDir = scratchDir.getAbsolutePath();
```

### 6.3.2 混杂

> 拒绝一半对象，一半数据结构。

### 6.3.3 隐藏结构

> 分析为什么

### 6.4 数据传送对象

> DTO(Data Transfer Objects)
