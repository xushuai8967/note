# Singleton 单例模式

## 简单的一个单例模式的实例
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
				if(singleton == null){
					singleton = new Singleton();
				}
		}
		return singleton;
	}

}
```
