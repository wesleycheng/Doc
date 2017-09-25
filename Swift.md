## Code convention & best practice

1. 把警告当做错误处理。</br>
2. 使用具有描述性的名称，并结合驼峰式命名规则给类方法和变量等命名。别名称(类，结构体，枚举和协议)首字母大写，而方法或者变量的首字母小写。</br>
3. 缩写和简写应该要尽量避免，缩写和简写中的所有字符大小写要一致。如：userID not userId </br>
4. 对于函数和初始化方法，建议给所有参数命名。 如：</br>
    <pre><code>func convertPointAt(column column:Int, row:Int) > CGPoint { ... } </code></pre>
5. 方法命名的时候要考虑方法体中的第一个参数的名称。 如：</br>
    <pre><code>func findBy(name: String) { ... }</code></pre>
6. 协议名称用来描述一些东西是什么的时候是名词，如：Collection, WidgetFactory。</br>
若协议名称用来描述能力应该以-ing, -able, 或 -ible结尾. 如：Equatable,Resizing.</br>
7. 当一个对象要实现协议一致性时，推荐使用 extension 隔离协议中的方法集.  如：</br>
<pre><code>extension MyViewcontroller: UIScrollViewDelegate {
    // UIScrollViewDelegate 方法
}</code></pre>
8. 无用的代码，包括Xcode生成的模板代码和占位符注释应该删除，除非是有目的性的保留这些代码。</br>
9. 减少不必要的引入，例如引入Foundation能满足的情况下不用引入UIKit。</br>
10. 缩进使用4个空格。</br>
11. 方法体的大括号和其他大括号 (if/else/switch/while等) 首括号和首行语句在同一行，尾括号新起一行。如：</br>
<pre><code>if user.isHappy {
    // xxx
} else {
    // xxx
}</code></pre>
12. : 左面不要空格，而右面需要保留空格，例外的是三元操作符 ? : 和空数组 [:]。 如：</br>
<pre><code>class TestDatabase: Database {
    var data: [String: CGFloat] = ["A": 1.2,"B": 3.2]
}</code></pre>
13. 代码本身应尽量起到注释的作用。当需要的时候，使用注释来解释阐明特定一块代码的用途，注释必须保持最新，过期的注释要及时删除。</br>
14. 给那些不打算被继承的类使用final 修饰符。</br>
15. 对于声明较长的函数时，在适当的位置换行并在第二行多添加一个缩进。</br>
16. 仅在闭包表达式参数在参数列表中最后一个时，使用尾随闭包表达式。闭包参数命名要有描述性。如：</br>
<pre><code>UIView.animateWithDuration(1.0) {
     self.myView.alpha=0
}

UIView.animateWithDuration(1.0, 
      animations: {
            self.myView.alpha = 0
       },
       completion: { finish in
            self.myView.removeFromSuperview()
       }
)</code></pre>
17. 优先使用Swift原生类型，可以根据需要使用Objective-C提供的方法。</br>
18. 定义常量使用 let 关键字，定义变量使用 var 关键字， 如果变量的值未来不会发生变化要使用常量。</br>
19. 静态方法和类别属性的工作原理类似于全局方法和全局属性，应该节制使用。</br>
20. 对空的数据和字典，使用类型注解。如：</br>
<pre><code>var names:  [String] = []
var lookup:  [String: Int] = [:]</code></pre>
21. 使用简洁的类型定义语法. 如：</br>
<pre><code>var deviceModels: [String]
var employees: [Int:String]
var faxNumber: Int?</code></pre>
Not:
<pre><code>var deviceModels: Array<String>
var employees: Dictionary<Int, String>
var faxNumber: Optional<Int></code></pre>
22. [weak self] 优于 [unowned self] 因为前者更更能明显地self 生命周期长于闭包块。显式延长生命周期优先于可选性拆包。如：</br>
<pre><code>resource.request().onComplete { [weak self] response in
    guard let strongSelf = self else {return}
    let model = strongSelf.updateModel(response) 
    strongSelf.updateUI(model)
}</code></pre>
23. 循环使用for-in表达式，而不使用 while 表达式 </br>
24. 条件判断时圆括号不是必须的，建议省略。Swift不强制每条语句有分号，建议省略。


