# Singleton ����ģʽ

�򵥵�һ������ģʽ��ʵ����
```java
public class Singleton {
  //��̬���� ������¼Ψһ�Ķ���
	public static Singleton singleton;
	//˽�еĹ��캯�� ֻ���Լ��ڲ��ܹ����ò�����ʵ��
	private Singleton(){
		
	}
	//���ⴴ��ʵ���ķ���
	public static Singleton getInstance(){
		if(singleton == null){
		//�����ǰ����Ϊ�յ�ʱ��֤����û��ʵ��������
			 singleton = new Singleton();
		}
		return singleton;
	}

}
```
��δ��뿴�������һ������ģʽ�����Ǵ�����©�����ڶ��̵߳Ļ����£�����ͬʱ����ִ��getInstance()��
������һ���߳��ж��굱ǰû��ʵ����׼������ʵ��ʱ������һ���߳�Ҳ����׼������ʵ��״̬����ʱ���Ͳ��ǵ�����

### �����Ľ�
```java
public class Singleton {
  //��̬���� ������¼Ψһ�Ķ���
	public static Singleton singleton;
	//˽�еĹ��캯�� ֻ���Լ��ڲ��ܹ����ò�����ʵ��
	private Singleton(){
		
	}
	//���ⴴ��ʵ���ķ���
	//�Ľ��������߳�ͬ��
	public static synchronized Singleton getInstance(){
		if(singleton == null){
		//�����ǰ����Ϊ�յ�ʱ��֤����û��ʵ��������
			 singleton = new Singleton();
		}
		return singleton;
	}

}
```
��getInstance()��Ϊ�߳�ͬ������ʱ�Ͳ�����ֶ��̻߳������ֵ�©����
�����µ��������ˣ��߳�ͬ��ʮ���������ܣ���Ӧ�ó���Ƶ������getInstance()ʱ����Ҫ���ǵ�����������

### ���ŸĽ����ռ�������

```java
public class Singleton {
  //��̬���� ������¼Ψһ�Ķ���
	public static Singleton singleton;
	//˽�еĹ��캯�� ֻ���Լ��ڲ��ܹ����ò�����ʵ��
	private Singleton(){
		
	}
	//���ⴴ��ʵ���ķ���
	//�Ľ���ֻ�е�һ�λ��ж��߳�ͬ���������Ч��
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