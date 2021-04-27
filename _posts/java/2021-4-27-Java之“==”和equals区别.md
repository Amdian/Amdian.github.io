---
layout: post
comments: true
categories: Java
---

* content
{:toc}

#### 一图胜千言
<img src="/static/img/java/2.jpg" align=left><br>

---

#### 实战
{% highlight ruby %}
	public static void main(String[] args) {
		// TODO Auto-generated method stub
		String a="小明";
		String b="小明";
		System.out.println(a==b);//结果为true
		System.out.println(a.equals(b));//结果为true
		
		String c = new String("小明");
		System.out.println(a==c);//结果为false
		System.out.println(b==c);//结果为false
		System.out.println(a.equals(c));//结果为true
		System.out.println(b.equals(c));//结果为true
	}
{% endhighlight %}

---

#### 探索谜团

<p>为什么在第一个例子中，用==的时候都为true，而在第二例子中，==却是false ?</p>
>其实，在java中会有一个字符串池。当采取直接赋值的方式创建一个字符串时，JVM会先去字符串池里面查找是否存在“小明”这个对象，如果不存在，则会创建一个“小明的对象”，然后将“小明”这个对象的引用地址返回给字符串常量 a；假如已经存在了，那么就直接返回这个对象的引用地址，就跟b那样，它就不会重新创建一个对象。因此在第一个例子中为什么用==会true，因为它们都是指向的同一个对象，所以会返回true。
<p>但是我们再来看第二例子，第二个有点不同的是，用了new来创建了新的对象，因此在字符串池中就会有两个对象，两个对象的值都一样，但是引用地址（对象）不同。所以用==就返回false。</p>

<p><font  size="3" color="#8B0000">因此我们可以总结一下</font></p>

== 是可以用判断两个是否为同一个对象 或者对于基本的数据类型的值是否相等。
equals 则可以用来判断值是否相等，不管两个是否为同一个对象，只要值相等，那么则返回true。