# javaad
java 进阶教程的笔记
2-1
异常处理：区别于面向过程和面向对象的一点




2-2
用try ....catch来处理的异常：①程序猿可以控制的异常
			    ②用户输入有误的情况
try{
	有可能出现错误的代码
}
catch(Exception e){
	System.out.println("有错误");

}
如果try里面有错误则执行catch里面的内容，并继续执行下面的内容，
这样程序就不会因错误而终止




2-3
用throws处理异常：①他的处理方式将异常抛给上一级处理
                   如果不能处理，最终抛给虚拟机处理
		  ②相对严重的异常，无法预料，无法完全避免

代码：
import java.util.Scanner;
public class A{
	public static void main(String[] args){
		B koukou=new B();
		koukou.b();
				
	}
}
class B{
	void b()throws Exception//会使koukou.b()出错，提示上一级处理错误
	{
		int a,b,c;
		Scanner in=new Scanner(System.in);
		a=in.nextInt();
		b=in.nextInt();
		c=a%b;
		System.out.println("余数为："+c);
	}
}




2-4

Finally:起到异常处理出口的作用，用在 try..catch的最后
        Finall不论catch会不会被执行都会被执行
	
import java.util.Scanner;
public class A{
	public static void main(String[] args){
		B koukou=new B();
		try{
		
			koukou.b();
		}
		catch(Exception e){
		System.out.println("有错误");
		}
		Finally{
			System.out.println("顺利执行");
		}	
	}
}

2-5
Equals方法
在java中比较中一般不用==来进行比较，而用equals

B b1=new B();
B b2=new B();
System.out.println(b1==b2);//输出False,因为==比较的是地址而非属性类型
System.out.println(b1.equals(b2));//输出false,在Object中equals与==一样，此时要根据需要进行重写



2-6
equals在一般情况下都需要覆盖自己想要的方法，
可以配合多态来实现比较强大的功能
public class L3_1
{
	public static void main(String[] args) 
	{
		B b1=new B(200);
		B b2=new B(200);
		//System.out.println(b1.equals(b2));
		
		C c1=new C(10);
		C c2=new C(100);
		System.out.println(c2.equals(c1));
	}
}
class B
{
   private int i;
   
	B(int i)
	{
       this.i=i;
	}
 
	public boolean equals(B b2)
	{
	    if(this.i==b2.i)
	    	return true;
	    else
	    	return false;
    }
}
class C extends B
{
	private int j;
	
	C(int j)
	{
	   super(j);
	   this.j=j;
	}

	public boolean equals(B b2)//不改写的话，子类中的变量不可以在调用父类中
	{					方法时用自己的变量
	    C c=(C)b2;//（强行向下转型）
		if(this.j==c.j)
	    	return true;
	    else
	    	return false;
    }
}
此程序中体现的内容：封装，继承，多态
封装：外类没有必要调用的成员就可以封装起来以保证安全性
继承：实现更多地equals方法
多态;实现程序的可扩展性




2-3
帮助文档的使用
4-1
集合类：是一个特殊的类，专门用来存放***其他类对象***的容器，
主要完成一些数据库与数据结构的功能。使我们的程序更加强大更加简单。
       
集合类的分类：
 1.List结构集合类：ArrayList LinkList Vector Stack

 2.Map结构集合类 HashMap HsahTable

 3.Set结构集合类 HashSet TreeSet
