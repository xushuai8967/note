# Singleton ����ģʽ

## �򵥵�һ������ģʽ��ʵ��
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
				if(singleton == null){
					singleton = new Singleton();
				}
		}
		return singleton;
	}

}
```
