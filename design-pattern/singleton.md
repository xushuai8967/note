# Singleton 单例模式

简单的一个单例模式的实例：
```java
public class Singleton {
  //静态对象 用来记录唯一的对象
	public static Singleton singleton;
	//私有的构造函数 只有自己内部能够调用并创建实例
	private Singleton(){
		
	}
	//对外创建实例的方法
	public static Singleton getInstance(){
		if(singleton == null){
		//如果当前对象为空的时候，证明还没有实例被创建
			 singleton = new Singleton();
		}
		return singleton;
	}

}
```
这段代码看似完成了一个单例模式，但是存在这漏洞，在多线程的环境下，可能同时调用执行getInstance()，
在其中一个线程判断完当前没有实例并准备创建实例时，另外一个线程也进入准备创建实例状态，这时，就不是单例了

### 做出改进
```java
public class Singleton {
  //静态对象 用来记录唯一的对象
	public static Singleton singleton;
	//私有的构造函数 只有自己内部能够调用并创建实例
	private Singleton(){
		
	}
	//对外创建实例的方法
	//改进后增加线程同步
	public static synchronized Singleton getInstance(){
		if(singleton == null){
		//如果当前对象为空的时候，证明还没有实例被创建
			 singleton = new Singleton();
		}
		return singleton;
	}

}
```
将getInstance()变为线程同步，这时就不会出现多线程环境出现的漏洞了
但是新的问题来了，线程同步十分消耗性能，在应用程序频繁调用getInstance()时，就要考虑到性能问题了

### 接着改进的终极方案：

```java
public class Singleton {
  //静态对象 用来记录唯一的对象
	public static Singleton singleton;
	//私有的构造函数 只有自己内部能够调用并创建实例
	private Singleton(){
		
	}
	//对外创建实例的方法
	//改进后，只有第一次会判断线程同步，提高了效率
	public static Singleton getInstance(){
		if(singleton == null){
			synchronized(Singleton.class){
				if(singleton == null){
					singleton = new Singleton();
				}
			}
		}
		return singleton;
	}

}
```