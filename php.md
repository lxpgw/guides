### 写在最前面

本规范参照[fig-standards](https://github.com/php-fig/fig-standards)进行编纂。

开发工具推荐 sublime text 3,推荐的工具为[sublime-phpfmt](https://github.com/dericofilho/sublime-phpfmt),推荐配置为:

	{
	"psr1":false,
	"psr2":true,
	"php_bin":"D:\\wamp\\bin\\php\\php5.5.12\\php.exe",
	// "indent_with_space":false,
	"format_on_save":false,
	"disable_auto_align":true
	}


即使用 PSR-2 规范。


## 1. 概览

* PHP代码文件__必须__以<?php标签开始,纯PHP代码文件必须省略最后的 ?> 结束标签

* 所有PHP文件必须使用Unix LF (linefeed)作为行的结束符

* PHP代码文件__必须__以不带BOM的 UTF-8 编码

* 命名空间以及类名必须符合 PSR 的自动加载规范 [PSR-4](https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-4-autoloader.md)

* 类的命名必须遵循 StudlyCaps 大写开头的驼峰命名规范

* 类中的常量所有字母都必须大写，单词间用下划线分隔

* 方法名称必须符合 camelCase 式的小写开头驼峰命名规范

* 代码缩进必须为4个空格(可以设置编辑器的tab为4个空格，如sublime设置 tab_size 为 4 )

* 每个 namespace 命名空间声明语句和 use 声明语句块后，必须插入一个空白行

* 类的花括号({) 和(}) 必须各自成一行

* 类的属性和方法必须添加访问修饰符(private, protected 和public), abstract 以及 final 必须声明在访问修饰符之前，而 static 必须声明在访问修饰符之后

* 控制结构的开始花括号({)必须写在声明的同一行，而结束花括号(})必须写在主体后自成一行

* 控制结构的开始左括号后和结束右括号前，都一定不能有空格符


一个符合上面的代码例子：

<?php
namespace Vendor\Model;

use FooInterface;
use BarClass as Bar;
use OtherVendor\OtherPackage\BazClass;

class Foo extends Bar implements FooInterface
{
	public function sampleFunctin($a, $b = null)
	{
		if ($a === $b) {
			bar();
		} elseif {
			$foo->bar($arg1);
		} else {
			BazClass::bar($arg2, $arg3);
		}
	}

	final public static function bar()
	{
		//method body
	}
}

## 2. 类和命名空间

命名空间以及类的命名必须遵循 PSR-0.

根据规范，每个类都独立为一个文件，且命名空间至少有一个层次：顶级的组织名称（vendor name）。

类的命名必须 遵循 StudlyCaps 大写开头的驼峰命名规范。

PHP 5.3及以后版本的代码必须使用正式的命名空间。

例如：


	<?php
	// PHP 5.3及以后版本的写法
	namespace Vendor\Model;

	class Foo
	{
	}

5.2.x及之前的版本应该使用伪命名空间的写法，约定俗成使用顶级的组织名称（vendor name）如 Vendor_ 为类前缀。

	<?php
	// 5.2.x及之前版本的写法
	class Vendor_Model_Foo
	{
	}

### 2.1 类的常量

类的常量中所有的字母都必须大写，词间以下划线分割。

	<?php
	namespace Vendor\Model;

	class Foo
	{
		const VERSION = '1.0.0';
		const DATE_APPROVED = '2014-12-28';
	}

### 2.2 属性

类的属性命名需遵循小写开头的驼峰式($camelCase), 每个属性都必须添加访问修饰符。


### 2.3 方法

所有类的方法名称必须符合 camelCase() 式的小写开头驼峰命名规范, 所有方法都必须添加访问修饰符。

方法名称后一定不能有空格符，其开始花括号必须独占一行，结束花括号也必须在方法主体后单独成一行。参数左括号后和右括号前一定不能有空格。

一个标准的方法声明可参照以下范例，留意其括号、逗号、空格以及花括号的位置。

	<?php
	namespace Vendor\Package;

	class ClassName
	{
	    public function fooBarBaz($arg1, &$arg2, $arg3 = [])
	    {
	        // method body
	    }
	}

### 2.4 方法的参数

参数列表中，每个参数后面必须要有一个空格，而前面一定不能有空格。

有默认值的参数，必须放到参数列表的末尾。

	<?php
	namespace Vendor\Package;

	class ClassName
	{
	    public function foo($arg1, &$arg2, $arg3 = [])
	    {
	        // method body
	    }
	}

参数列表可以分列成多行，这样，包括第一个参数在内的每个参数都必须单独成行。

拆分成多行的参数列表后，结束括号以及方法开始花括号 必须 写在同一行，中间用一个空格分隔。

	<?php
	namespace Vendor\Package;

	class ClassName
	{
	    public function aVeryLongMethodName(
	        ClassTypeHint $arg1,
	        &$arg2,
	        array $arg3 = []
	    ) {
	        // method body
	    }
	}

### 2.5 方法及函数调用

方法及函数调用时，方法名或函数名与参数左括号之间一定不能有空格，参数右括号前也一定不能有空格。每个参数前一定不能有空格，但其后必须有一个空格。

	<?php
	bar();
	$foo->bar($arg1);
	Foo::bar($arg2, $arg3);

参数可以分列成多行，此时包括第一个参数在内的每个参数都必须单独成行。

	<?php
	$foo->bar(
	    $longArgument,
	    $longerArgument,
	    $muchLongerArgument
	);

### 2.6 扩展与继承

关键词 extends 和 implements 必须写在类名称的同一行。

## 3 控制结构

控制结构的基本规范如下：

* 控制结构关键词后必须有一个空格。
* 左括号 ( 后一定不能有空格。
* 右括号 ) 前也一定不能有空格。
* 右括号 ) 与开始花括号 { 间一定有一个空格。
* 结构体主体一定要有一次缩进。
* 结束花括号 } 一定在结构体主体后单独成行。

> 每个结构体的主体都必须被包含在成对的花括号之中， 这能让结构体更加结构话，以及减少加入新行时，出错的可能性。

### 3.1 if 、 elseif 和 else

标准的 if 结构如下代码所示，留意 括号、空格以及花括号的位置， 注意 else 和 elseif 都与前面的结束花括号在同一行。

	<?php
	if ($expr1) {
	    // if body
	} elseif ($expr2) {
	    // elseif body
	} else {
	    // else body;
	}

应该使用关键词 elseif 代替所有 else if ，以使得所有的控制关键字都像是单独的一个词。

### 3.2 switch 和 case

标准的 switch 结构如下代码所示，留意括号、空格以及花括号的位置。 case 语句必须相对 switch 进行一次缩进，而 break 语句以及 case内的其它语句都 必须 相对 case 进行一次缩进。 如果存在非空的 case 直穿语句，主体里必须有类似 // no break 的注释。

	<?php
	switch ($expr) {
	    case 0:
	        echo 'First case, with a break';
	        break;
	    case 1:
	        echo 'Second case, which falls through';
	        // no break
	    case 2:
	    case 3:
	    case 4:
	        echo 'Third case, return instead of break';
	        return;
	    default:
	        echo 'Default case';
	        break;
	}

### 3.3 while 和 do while

一个规范的 while 语句应该如下所示，注意其 括号、空格以及花括号的位置。

	<?php
	while ($expr) {
	    // structure body
	}

标准的 do while 语句如下所示，同样的，注意其 括号、空格以及花括号的位置。

	<?php
	do {
	    // structure body;
	} while ($expr);

### 3.4 for

标准的 for 语句如下所示，注意其 括号、空格以及花括号的位置。

	<?php
	for ($i = 0; $i < 10; $i++) {
	    // for body
	}

### 3.5 foreach

标准的 foreach 语句如下所示，注意其 括号、空格以及花括号的位置。

	<?php
	foreach ($iterable as $key => $value) {
	    // foreach body
	}

### 3.6 try, catch

标准的 try catch 语句如下所示，注意其 括号、空格以及花括号的位置。

	<?php
	try {
	    // try body
	} catch (FirstExceptionType $e) {
	    // catch body
	} catch (OtherExceptionType $e) {
	    // catch body
	}

## 闭包

闭包声明时，关键词 function 后以及关键词 use 的前后都必须有一个空格。

开始花括号必须写在声明的同一行，结束花括号必须紧跟主体结束的下一行。

参数列表和变量列表的的左括号后和右括号前，必须不能有空格。

参数和变量列表中，逗号前必须不能有空格，而逗号后必须要有空格。

闭包中有默认值的参数必须放到列表的后面。

	<?php
	$closureWithArgs = function ($arg1, $arg2) {
	    // body
	};

	$closureWithArgsAndVars = function ($arg1, $arg2) use ($var1, $var2) {
	    // body
	};

参数列表以及变量列表可以分成多行，这样，包括第一个在内的每个参数或变量都必须单独成行，而列表的右括号与闭包的开始花括号必须放在同一行。

以下几个例子，包含了参数和变量列表被分成多行的多情况。

	<?php
	$longArgs_noVars = function (
	    $longArgument,
	    $longerArgument,
	    $muchLongerArgument
	) {
	   // body
	};

	$noArgs_longVars = function () use (
	    $longVar1,
	    $longerVar2,
	    $muchLongerVar3
	) {
	   // body
	};

	$longArgs_longVars = function (
	    $longArgument,
	    $longerArgument,
	    $muchLongerArgument
	) use (
	    $longVar1,
	    $longerVar2,
	    $muchLongerVar3
	) {
	   // body
	};

	$longArgs_shortVars = function (
	    $longArgument,
	    $longerArgument,
	    $muchLongerArgument
	) use ($var1) {
	   // body
	};

	$shortArgs_longVars = function ($arg) use (
	    $longVar1,
	    $longerVar2,
	    $muchLongerVar3
	) {
	   // body
	};

注意，闭包被直接用作函数或方法调用的参数时，以上规则仍然适用。

<?php
$foo->bar(
    $arg1,
    function ($arg2) use ($var1) {
        // body
    },
    $arg3
);

## 附加

参考

[php-fig的中文翻译](https://github.com/PizzaLiu/PHP-FIG)

[php-fig项目地址](https://github.com/php-fig/fig-standards)